---
layout: post
title: Bug with Set and Get Accessor in .Net 3.5
tags: 
category: General
---
I spent a few hours scratching my head on this one... So I thought I would blog about it in case someone else had the same headache.

Assume you have a class, and you are wanting to use the INotifyPropertyChanged interface so that when you bind to an instance of the class, you get the magic sauce of binding to do you updates to the UI. Well, I had a special instance where I wanted one of the properties of the class to add some additional formatting to itself whenever someone changed its value (see the code below).

 
 ~~~

class Test: INotifyPropertyChanged 
{ 
    private string_inputValue; 

    public stringInputValue 
    { 
        get 
       { 
            return_inputValue; 
        } 
        set 
       { 
            if(value!= _inputValue) 
            { 
                _inputValue = value+ "Extra Stuff"; 
                NotifyPropertyChanged("InputValue");         
            } 
        } 
    } 

    public eventPropertyChangedEventHandler PropertyChanged; 

    public voidNotifyPropertyChanged(stringinfo) 
    { 
        if(PropertyChanged != null) 
        { 
            PropertyChanged(this, newPropertyChangedEventArgs(info)); 
        } 
    } 
} 
~~~
 

Everything looked fine, but when I ran it in my WPF project, the textbox I was binding to would not update? I couldn’t understand it! I thought the code made sense, so why wasn’t it working? Eventually StackOverflow came to the rescue, where I was told that it was a bug in the .Net 3.5 Runtime and that a fix was scheduled in .Net 4

For those who have the same problem, here is the workaround… You need to put the NotifyPropertyChanged method on the application thread!

~~~
public string InputValue
{
    get
    {
        return _inputValue;
    }
    set
    {
        if (value != _inputValue)
        {
            _inputValue = value + "Extra Stuff";
            //
            // React to the type of measurement
            //
            Application.Current.Dispatcher.BeginInvoke((Action)delegate
            {
                NotifyPropertyChanged("InputValue");
            });                
        }                
    }
}
~~~