---
layout: post
title: Accessing the Dispatcher Thread from your ViewModel
tags: 
category: General
---
A little snippet that might help anyone using the MVVM pattern. If we want to marshal something through to the Dispatcher Thread from a view model we can do the following  within the ViewModel class…

 

        private void SendingToTheDispatcherThread()
        {
            Dispatcher dispatcher = Application.Current.Dispatcher;


            if (!dispatcher.CheckAccess())
            {
                dispatcher.BeginInvoke((Action)(() =>
                                                    {
                                                        // put code for the dispatched here
                                                    }));
            }
            else
            {
                // put code for the dispatched here
            }
        }