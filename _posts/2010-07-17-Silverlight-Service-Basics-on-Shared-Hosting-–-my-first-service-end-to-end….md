---
layout: post
title: Silverlight Service Basics on Shared Hosting – my first service end to end…
tags: 
category: General
---
So today I finally got around to playing a bit more with Silverlight. F# has been taking most of my spare time and I felt I needed to branch out into something different for a day or two…

Now, before I go into this post… my disclaimer… I am a Silverlight noob – in fact I have focussed most of my development time at normal applications so the whole internet is a bit of a mystery to me… that being said I had some very definite goals for this posting…

Setup my server so that it would work with the services correctly
Initiate a service that accepted a string to the server and sent back a bool
Step 1 – Setup of the server

The setup on my server was fairly simple…

1) First thing is to create the actual directory on the server. I did this using filezilla and placed the directory under the wwwroot folder.

 

2) I then had to setup a virtual directory. Setting up the virtual directory was necessary so that the instance of my silverlight application would be separate to the rest of my site. The way it was explained to me was if I didn’t setup the virtual directory, when someone visited my site, it would be accessing the root (wwwroot) instead of the individual application (I don’t know if this makes sense… but that was how it was explained or atleast how I understood it).

 

2010-10-03 04-00-53 PM

So… select I went through the control panel for my server and clicked on Virtual Directories…

2010-10-03 04-01-18 PM

Then added a new virtual directory….

2010-10-03 04-01-31 PM

And just made sure the details were right…

That all being done, the server side was 100% (keeping in my mind sever already support .Net 3.5 etc).

Step 2 – The Silverlight Application Creation

So the next step is to actually create the application. I did it through VS2010 and created a new project.

2010-10-03 04-08-32 PM

You’ll then be asked what version of Silverlight you want the project to be – in this instance I am going to do version 4.

2010-10-03 04-11-16 PM

And then you will be taken into your dev environment in VS2010.

For the purposes of this demo I am simply going to create a single form with a button on it, that when a user clicks, it triggers a service and pops up a message box once a response has been received from the server.

Step 3 - Setting up the Service

 

2010-10-03 04-15-24 PM

First thing is to create the folder where your service will located.

2010-10-03 04-16-22 PM

Then add a Silverlight-enabled WCF Service as a child to the Services folder…

Now I want to go and make a method under my “Service1” that when it is called returns a string "Hello Service again build 2".

I do this my going to the service and viewing the code.

2010-10-03 04-33-50 PM

I then go and edit the code so it looks as follows…

using System.ServiceModel;
using System.ServiceModel.Activation;

namespace HelloWorldService.Web.Services
{
    [ServiceContract(Namespace = "")]
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
    public class Service1
    {
        [OperationContract]
        public string GetMyMessage()
        {
            // Add your operation implementation here
            return "Hello Service again build 2";
        }        

        // Add more operations here and mark them with [OperationContract]
    }
}
 

This being done I still have a bit more customizing to do to the service. Namely I need to specify a custom host factory. To do this I go and view the markup for the service. Right click on the service and you will get a menu as shown below…

2010-10-03 04-36-31 PM

When you select view markup you need to add to the markup where the factory is located. Change the markup to have the following in it…

Factory="HelloWorldService.Web.Services.CustomHostFactory"
 

So the entire markup for the service might look something like the following…

<%@ ServiceHost Language="C#" Debug="true" Service="HelloWorldSL.Web.Services.Service1" CodeBehind="Service1.svc.cs"  Factory="HelloWorldService.Web.Services.CustomHostFactory"%>

Now we have specified a Factory, but we haven’t yet created one so we now have to create a Custom Host Factory. Do this by adding a CSharp file under the services folder called “CustomHostFactory.cs”.

2010-10-03 04-42-27 PM

Then put the following code in CustomHostFactory.cs

 

using System;
using System.ServiceModel.Activation;
using System.ServiceModel;

namespace HelloWorldSL.Web.Services
{
    public class CustomHostFactory : ServiceHostFactory
    {
        protected override ServiceHost CreateServiceHost(Type serviceType, Uri[] baseAddresses)
        {
            if (baseAddresses.Length == 1)
            {
                return new CustomHost(serviceType, baseAddresses[0]);
            }
            else
            {
                return new CustomHost(serviceType, baseAddresses[1]);
            }
        }
    }

    public class CustomHost : ServiceHost
    {
        public CustomHost(Type serviceType, params Uri[] baseAddresses)
            : base(serviceType, baseAddresses)
        {
        }

        protected override void ApplyConfiguration()
        {
            base.ApplyConfiguration();
        }
    }
}
 

At this point you will notice that if you try and compile the solution you get an error…

Error    1    The type name 'ServiceHostFactory' could not be found. This type has been forwarded to assembly 'System.ServiceModel.Activation, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35'. Consider adding a reference to that assembly.    c:\users\mark\documents\visual studio 2010\Projects\HelloWorldService\HelloWorldService.Web\Services\CustomHostFactory.cs    7    38    HelloWorldService.Web

This is because the web project is using the .Net4 runtime. We need to change this to .Net3.5

2010-10-04 07-11-56 AM

Because we have now changed from .Net4 to 3.5 you will also need to remove the references in the solution that are only compatible with 4 (i.e. Microsoft.CSharp).

 

Step 4 – Referencing the Service

We now have created these services, but somehow need to reference them "in our “Client Side”.

If your tried to add the service reference immediately you will get errors. I believe this is mainly because we have gone from .Net4 to .Net3.5, so before we can actually add the service, we need to change our “Web.config” file so it is compatible.

First of all find the line with the following…

<serviceHostingEnvironment aspNetCompatibilityEnabled="true" multipleSiteBindingsEnabled="true"/>
 

and remove the multipleSiteBindingsEnabled so that it looks as follows…

 

   <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>

 

Then look for the following section…

        <behaviors>
            <serviceBehaviors>
                <behavior name="">
                    <serviceMetadata httpGetEnabled="true"/>
                    <serviceDebug includeExceptionDetailInFaults="false"/>
                </behavior>
            </serviceBehaviors>
        </behaviors>
 

and if it does not have a valid name for the behavior, give it one so that it will look like this….

        <behaviors>
            <serviceBehaviors>
                <behavior name="HelloWorldService.Web.Services.Service1Behavior">
                    <serviceMetadata httpGetEnabled="true"/>
                    <serviceDebug includeExceptionDetailInFaults="false"/>
                </behavior>
            </serviceBehaviors>
        </behaviors>
 

Finally look for the actual service…

        <services>
            <service name="HelloWorldService.Web.Services.Service1">
                <endpoint address="" binding="customBinding" bindingConfiguration="HelloWorldService.Web.Services.Service1.customBinding0" contract="HelloWorldService.Web.Services.Service1"/>
                <endpoint address="mex" binding="mexHttpBinding" contract="IMetadataExchange"/>
            </service>
        </services>
 

And change it to have the following….

        <services>
            <service behaviorConfiguration="HelloWorldService.Web.Services.Service1Behavior" name="HelloWorldService.Web.Services.Service1">
                <endpoint address="" binding="customBinding" bindingConfiguration="HelloWorldService.Web.Services.Service1.customBinding0" contract="HelloWorldService.Web.Services.Service1"/>
                <endpoint address="mex" binding="mexHttpBinding" contract="IMetadataExchange"/>
            </service>
        </services>
 

Now we have configured the Web.config file correctly, we can actually look at adding the service reference. To do this we need to add a service reference to the “HelloWorldService” project. Right click on the project and select the “Add Service Reference” option.

2010-10-04 07-16-14 AM 

You will now get the “Add Service Reference Dialog”…

2010-10-04 07-17-39 AM

Click Discover, select the service and click OK. This will add the service to the “Client Side” of the project.

So we are almost there… we just need to do a bit of configuring on the client side. The first thing we need to do is add the “ServiceProxyHelper.cs” to the client side project.

2010-10-04 07-46-49 AM

And put the following code behind it…

using System;
using System.Windows;
using HelloWorldService.ServiceReference1;

namespace HelloWorldService
{
    public class ServiceProxyHelper
    {
        public static Service1Client CreateService1Proxy(string serviceName)
        {
            Uri Address = new Uri(Application.Current.Host.Source, "../Services/" + serviceName + ".svc");
            return new Service1Client("CustomBinding_Service1", Address.AbsoluteUri);
        }
    }
}
Finally in the code behind I am going to briefly demonstrate calling the service – obviously there would be better ways to structure the code (i.e. MVVM) but this is really just the cheap & nasty way…

using System;
using System.Windows;
using System.Windows.Controls;

namespace HelloWorldService
{
    public partial class MainPage : UserControl
    {
        public MainPage()
        {
            InitializeComponent();
        }

        private void button1_Click(object sender, RoutedEventArgs e)
        {
            ServiceReference1.Service1Client s1c = ServiceProxyHelper.CreateService1Proxy("Service1");
            s1c.GetMyMessageCompleted += new EventHandler<ServiceReference1.GetMyMessageCompletedEventArgs>(s1c_GetMyMessageCompleted);
            s1c.GetMyMessageAsync();            
        }

        void s1c_GetMyMessageCompleted(object sender, ServiceReference1.GetMyMessageCompletedEventArgs e)
        {
            if (e.Error == null)
            {
                MessageBox.Show(e.Result.ToString());
            }
            else
            {
                MessageBox.Show("Error - " + e.Error.Message);
            }
        }
    }
}
Now if you run the solution you will get something like this…

2010-10-04 07-52-49 AM

And there you go… we have created a basic service, configured it to work and it is operating correctly on our localhost – now we just need to publish it to the live site…

Step 5 – Publishing to the live site

Publishing is very easy in VS2010… simply right click on “HelloWorldService.Web”

2010-10-04 08-24-04 AM

This bring up the publish screen…

2010-10-04 08-23-35 AM

And fill in your details, making sure you publish to the virtualized directory…

And then test it…

2010-10-04 08-26-45 AM

 

And that’s it..
