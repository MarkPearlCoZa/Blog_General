---
layout: post
title: Hello Reactive Extensions
tags: 
category: General
---
I have seen the rx demos by Bart De Smet and was blown away by the potential that I think they hold – however I just haven’t had time up till now to have a look at them in any depth. Today I finally set some time aside and got a 10 000 foot view of them.

So my plan is for the next few days to develop an application in WPF that makes use of reactive extensions as a dummy project… Today I just wanted to get the basics working, and after going through an very good lab on rx was able to get a very basic example working…

All that the code does below is update a label when text is inputted into a textbox on a wpf form… early days, but lets see how we can develop this simple example to be a useful tool

 

using System;
using System.Reactive.Linq;
using System.Windows;
using System.Windows.Controls;

namespace WpfApplication6
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

        private void Window_Loaded(object sender, RoutedEventArgs e)
        {
            var input = (from evt in Observable.FromEventPattern<EventArgs>(this.textBox1, "TextChanged")
                         select ((TextBox)evt.Sender).Text).DistinctUntilChanged();

            var inputSubscription = input.Subscribe(evt => { label1.Content = evt; });            
        }
    }
}