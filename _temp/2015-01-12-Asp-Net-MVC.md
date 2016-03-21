---
layout: post
title: Asp.Net MVC Notes
tags: MVC
category: General
---

#### Basics ####

When a http request is made, the following basic flow happen...

MVC Route Handler > Controller  

The controller determines the action, if the action result returns a view, the view renderer will return the correct view.

#### Passing information from Controller to View ####

- The ViewBag  
- ViewDataDictionary  
- Strongly typed views with a view model  

Strongly typed views with a view model  

~~~
@using Guestbook.Models  	// Where the model is stored
@model TypeOfModel		// The type of the model  
  
...
  
<div> @model.FieldName </div>
~~~

---------------------------------------------------------------------------------

#### Dependency Injection with Controllers ####

[Asp.Net Controller Dependency Injection for Beginners](http://www.codeproject.com/Articles/560798/ASP-NET-MVC-Controller-Dependency-Injection-for-Be)

##### Manual Dependency Injection #####

Assume we have removed the default constructor on the home controller and instead our home controller has a dependency on persistenceService. We can manually get dependency injection working by doing the following.

- Create a custom controller factory  
- Wire up the builder current factory to the custom controller  

Create the following custom controller factory...  

~~~
public class CustomControllerFactory : IControllerFactory
{
	readonly persistenceService _persistenceService;

	public CustomControllerFactory()
	{
		_persistenceService = new persistenceService();
	}

	public IController CreateController(RequestContext requestContext, string controllerName)
	{
		if (controllerName.ToLowerInvariant().StartsWith("home"))
		{
			var controller = new HomeController(_persistenceService);
			return controller;
		}

		var defaultFactory = new DefaultControllerFactory();
		return defaultFactory.CreateController(requestContext, controllerName);
	}

	public SessionStateBehavior GetControllerSessionBehavior(RequestContext requestContext, string controllerName)
	{
		return SessionStateBehavior.Default;
	}

	public void ReleaseController(IController controller)
	{
		var disposable = controller as IDisposable;
		if (disposable != null)
		{
			disposable.Dispose();
		}
	}
}
~~~

In the global.asax.cs file make the following changes...

~~~
private void RegisterCustomControllerFactory()
{
	IControllerFactory controllerFactory =new CustomControllerFactory();
	ControllerBuilder.Current.SetControllerFactory(controllerFactory);
}


protected void Application_Start()
{
	RegisterCustomControllerFactory();
	...
}
~~~

#### Using an IOC container for Dependency Injection ####

- Add Unity.Mvc4 to the project via nuget  
- Register the types in the Bootstrapper.cs file  

#### Using Dependency Injection for Views ####

For dependency injection in views you need to use property injection.  

Create a class that the view will inherit from...  

~~~
public class DependencyResolvedBasePage : WebViewPage
{
	[Dependency]
	public IDependentService DependentService {get; set;}

	public ovveride void Execute()
	{
	}
}
~~~

In the view have something like...  

~~~
@inherits DependencyResolvedBasePage
...
~~~


