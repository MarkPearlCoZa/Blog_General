---
layout: post
title: MVVM Light Notes
tags: Frameworks
category: Tech
---

#### General Components ####


#### Notifying when a property has changed ####

~~~
public bool ExampleProperty
{
    get
    {
	return _exampleProperty;
    }
    set
    {
	_exampleProperty = value;
	RaisePropertyChanged(() => ExampleProperty);
    }
}
~~~

The above approach allows for easy safe refactoring.

~~~
public bool ExampleProperty
{
    get
    {
	return _exampleProperty;
    }
    set
    {
	_exampleProperty = value;
	RaisePropertyChanged("ExampleProperty");
    }
}
~~~

The above is an alternative that doesn't allow for as safe a refactoring.



#### Extras ####

Simple IOC - a simple IOC container for DI

##### EventToCommand #####

Handles the conversion of events to commands. Useful to understand behaviors vs actions. A behavior is standalone. An action is always attached to a trigger. When a trigger is actuated, it executes a command.

InvokeCommandAction is similar to EventToCommand with a few restrictions.

##### Simple IOC #####

###### Basic Example ######

~~~
SimpleIoc.Default.Register<IDataService, DataService>();
var isRegisterd = SimpleIoc.Default.IsRegistered<IDataService>(); //true
var isCreated = SimpleIoc.Default.ContainsCreated<IDataService>(); //false
var instance = SimpleIoc.Default.GetInstance<IDataService>();
~~~

###### Registering ######

Good practice to keep registering of dependencies in a central location. Typically this is done in the ViewModelLocator.

###### Deregistering ######

To optimize memory usage you can unregister components when they are no longer needed. If you are going to do this you should embrace the fact that the SimpleIOC will be tightly coupled to the UI layer.

~~~
SimpleIoc.Default.Unregister<IDialogService>(this);
SimpleIoc.Default.Unregister<IDialogService>("key1");
~~~

###### Getting All Created Instances ######

- Does not force creation of instances  
- Only existing instances are returned

~~~
var allInstances - SimpleIoc.Default.GetAllInstances<IDataService>();
~~~

###### Get All Instances ######

- Forces the creation of one default instance per registered class

~~~
var allInstances = SimpleIoc.Default.GetAllCreatedInstances<IDataService>();
~~~

##### Microsoft.Practices.ServiceLocation #####

ServiceLocation is a standard, which can potentially reduce coupling of the Ioc framework to the system.

~~~
ServiceLocator.SetLocatorProvider(() => SimpleIoc.Default);
ServiceLocator.Current.GetInstance<IDataService>();
~~~

#### Code Snippets ####

- inpc : adds a observable property  
- locatorproperty : adds a viewmodel property to the ViewModelLocator  
- prop : adds a attached or dependency property (WPF style)  
- relay : adds a relay command  
- slprop : adds a attached or dependency property (Silverlight style)  
- vm : adds an access to the ViewModel inside the View (DataContext)

#### References ####

[Pluralsight Course](http://www.pluralsight.com/courses/mvvm-light-toolkit-fundamentals)  
[CodePlex Project](https://mvvmlight.codeplex.com/)  
[MVVM Palindrome](http://davisnw.github.io/mvvm-palindrome/)  
