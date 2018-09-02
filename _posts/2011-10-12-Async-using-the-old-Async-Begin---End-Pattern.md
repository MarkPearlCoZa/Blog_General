---
layout: post
title: Async using the old Async Begin - End Pattern
tags: 
category: General
---
In the last few weeks I have had the pleasure of familiarising myself with various async patterns in C#. After going through the different approaches one gets a feel for how far we have come since the .Net 1 days. One particular pattern that I was not familiar with implementing but which has been available since the beginning of .Net is what I call the Async Begin / End Pattern.

Since my interest is really making calls asynchronously so that I don’t block the UI thread - from what I can tell this is one of the more complicated approaches to achieve this, but useful to know of where we have come from.

So the approach I am going to illustrate is one where we pass a delegate for a callback method to BeginInvoke. The method is executed on a ThreadPool thread when the asynchronous call completes. The callback method calls EndInvoke.

Let’s look at the synchronous implementation first…
Take a WPF project with one window and a button with a click event behind it.

Implement the following code…

using System.Threading;
using System.Windows;

namespace WpfApplicationTemp
{  
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();           
        }

        private void button1_Click(object sender, RoutedEventArgs e)
        {
            MessageBox.Show(DoThis());
        }

        public string DoThis()
        {
            Thread.Sleep(5000);
            return "Hello";
        }        
    }
}
 

If I were to run this application and click the button, everything would freeze for 5 seconds – while the DoThis method is called – then a message box would pop up with the return result. So a perfect scenario to make things asynchronous.

Making it Asynchronous using the Begin / End Pattern
First step would be to declare a delegate with a signature that matches the signature of the method we want to make asynchronous. In this case we want to make DoThis() method asynchronous so we would do something like the following…

public delegate string AsyncMethodCaller();
We then want remove our synchronous code and declare the AsyncMethodCaller at the point where we would initiate the async call and implement a callback method. In this case it would be in the button click event.

private void button1_Click(object sender, RoutedEventArgs e)
{
    AsyncMethodCaller caller = new AsyncMethodCaller(DoThis);
    IAsyncResult result = caller.BeginInvoke(new AsyncCallback(CallBackMethod), null);                            
}

public void CallBackMethod(IAsyncResult ar)
{
    AsyncResult result = (AsyncResult)ar;
    AsyncMethodCaller caller = (AsyncMethodCaller)result.AsyncDelegate;
    string returnValue = caller.EndInvoke(result);
    MessageBox.Show(returnValue);
}
 

And there we have it, we have made a synchronous method get executed asynchronously. Personally I don’t like this approach, it seems fairly complicated and has a lot of extra code that hides the core purpose of what we are trying to achieve, but it does illustrate the Begin End Pattern so mission accomplished.

For those that are wanting the entire code… here it is…

using System;
using System.Runtime.Remoting.Messaging;
using System.Threading;
using System.Windows;

namespace WpfApplicationTemp
{  
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();           
        }

        private void button1_Click(object sender, RoutedEventArgs e)
        {
            AsyncMethodCaller caller = new AsyncMethodCaller(DoThis);
            IAsyncResult result = caller.BeginInvoke(new AsyncCallback(CallBackMethod), null);                            
        }

        public void CallBackMethod(IAsyncResult ar)
        {
            AsyncResult result = (AsyncResult)ar;
            AsyncMethodCaller caller = (AsyncMethodCaller)result.AsyncDelegate;
            string returnValue = caller.EndInvoke(result);
            MessageBox.Show(returnValue);
        }


        public string DoThis()
        {
            Thread.Sleep(5000);
            return "Hello";
        }

        public delegate string AsyncMethodCaller();
    }
}
 

I would also recommend reading the documentation on MSDN explaining “Calling Synchronous Methods Asynchronously” which illustrates other implementations of the pattern and explains it in further detail.