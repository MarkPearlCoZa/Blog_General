---
layout: post
title: Simplifying Asynchronous Programming in C#
tags: 
category: General
---
I have dabbled in async programming in the past but never put any real effort into understanding how things worked. With the new async features in .Net 5 I thought I would give it a look. Here is a quick example of one of the features you can expect in the new framework and how it can make our life easier.

The best way to illustrate this is to make a simple WPF application as follows…

In the past
If we had the following small WPF application with just one window / form…

AsyncExample (Running) - Microsoft Visual Studio (Administrator)_2011-10-11_07-13-09

The XAML code for the window

<Window x:Class="AsyncExample.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        Title="MainWindow" Height="350" Width="525">
    <Grid Height="72" Width="149">        
        <Button Click="Button_Click">
            <TextBlock Name="myTB" Text="Click Me"/>
        </Button>
    </Grid>
</Window>
 

And the code behind for the window…

using System;
using System.Threading;
using System.Windows;

namespace AsyncExample
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private void Button_Click(object sender, RoutedEventArgs e)
        {
            myTB.Text = "Starting...";
            DateTime result = TakeAWhile();
            myTB.Text = result.ToString();
        }

        private DateTime TakeAWhile()
        {            
            Thread.Sleep(2000);
            return DateTime.Now;
        }
    }
}
 

Expected Behaviour

When running this app one would expect the following… if the user clicked the button the text would change to starting, it would then wait two seconds and display the date/time that it was completed.

Actual Behaviour

The problem with the above code is that because we are doing all this work on the UI thread we don’t get a responsive application – so what it actually happens on my machine is when I click on the button, the form freezes for two seconds (at which point if I try and drag it I get a “not responding” message) and then the button updates with the date / time.

Solving the problem using the async & awaits keywords
Introducing the async & await can simplify the problem

The Async keyword in a nutshell means the following

That within the scope of where the async keyword is used, you are allowed to use the await await keyword
The compiler will automatically rewrite the method from a synchronous form into a asynchronous form in IL code
Taking the same form as we had in the previous example and adjusting the code behind to use the async and await keyword we get something that looks like the following…

using System;
using System.Threading;
using System.Threading.Tasks;
using System.Windows;

namespace AsyncExample
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private async void Button_Click(object sender, RoutedEventArgs e)
        {
            myTB.Text = "Starting...";
            DateTime result = await TaskEx.Run(() => TakeAWhile());
            myTB.Text = result.ToString();
        }

        private DateTime TakeAWhile()
        {            
            Thread.Sleep(2000);
            return DateTime.Now;
        }
    }
}
 

Note that we have modified the Button_Click method to have the async keyword and then at the point where we call TakeAWhile we use the await keyword followed by TaskEx.Run (important to note that TaskEx will be renamed to Task in the final release).

Running the adjusted code when I get to the point where it reaches the await keyword, the application fires up another thread and runs the TakeAWhile method on a different thread, leaving my UI Thread unblocked and responsive – also leaving me with the experience that I would expect when clicking on the button.

So while this was possible in the past using background workers or threads, the new async and await keywords definitely simplify the code and make it seem more normal to read.

If you are interested in learning more about this topic visit the Microsoft Parallel Computing Site.