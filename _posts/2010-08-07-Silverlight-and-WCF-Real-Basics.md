---
layout: post
title: Silverlight and WCF Real Basics
tags: 
category: General
---
So I am not a web developer! I have never been one but Silverlight keeps popping in my head as the next big thing on the Microsoft stack and I would hate to “miss the boat” (I am sure some C developer said that 10 years ago as well).

Today I thought I would get a little wet with Silverlight & WCF. Up to now I have been working in WPF so I am not scared of XAML and am surprised to say that I actually enjoy it. I have however never worked with WCF so for me that will be the learning curve.

My project objective today:

Create a Silverlight project with a single button on it which when clicked calls a WCF service and display the message passed by the service to a message box.

Creating the Initial Project (VS2010)

First of all I create a new project in Visual Studio. I select a Silverlight Application and because my server only supports up to .Net Framework 3.5 I will select that as my targeted framework.

2010-05-12 02-49-53 PM

Once I click OK, it will then prompt me on the new web project name and the version of Silverlight that I will target. All pretty simple stuff.

2010-05-12 02-50-08 PM

Once I click OK, it then creates a Visual Studio solution with two projects, the first being my Silverlight Application, and the second being SilverlightApplication.Web project. The Silverlight Application is what will run on the end user side, the SilverlightApplication.Web project is what will be running on my Server.

2010-05-12 02-50-31 PM

I now drag a button on my MainPage and place a click event in the code behind. The code is pretty simple and will look something like the code below.

namespace SilverlightApplication6
{
    public partial class MainPage : UserControl
    {       

        public MainPage()
        {            
        }

        private void button1_Click(object sender, RoutedEventArgs e)
        {         
        }        
        
    }
}
I now need to make a WCF Service that my Silverlight application can call. I do this by selecting my .Web project and adding a new item. It will then bring up a dialog prompting what new item you want to add, and I select Silverlight under the Visual C# section of Installed Templates, and then select the item type to be a Silverlight-enabled WCF Service. For now I am just going to use the default name – Service1.svc

2010-05-12 02-51-15 PM

Once I have added the service to my .Web project, I need to go and customize the service to return the data I want. The service by default will look something like the code below…

namespace SilverlightApplication6.Web
{
    [ServiceContract(Namespace = "")]
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
    public class Service1
    {
        [OperationContract]
        public void DoWork()
        {
            // Add your operation implementation here
            return;
        }

        // Add more operations here and mark them with [OperationContract]
    }
}
In this scenario I am going to change the DoWork method to instead be called GetMyMessage and return a string. After making modifications to the code it will look like the code below…

public class Service1
    {
        [OperationContract]
        public string GetMyMessage()
        {
            // Add your operation implementation here
            return "Hello World from a Service";
        }

        // Add more operations here and mark them with [OperationContract]
    }
 

I now want to make this service accessible to my Silverlight application. So I go to my application and select the “Service References” section and a window appears that asks me what service I want to add.

2010-05-12 02-52-20 PM

Note – You need to build the project where your service is located if you want to make it visible in the dialog above.

Once you have added the service, it will be accessible in code. You can reference the service from the code behind of the Mainform as shown in my code snippet below…

namespace SilverlightApplication6
{
    public partial class MainPage : UserControl
    {
        private ServiceReference1.Service1Client s1c = new ServiceReference1.Service1Client();

        public MainPage()
        {
            InitializeComponent();            
            s1c.GetMyMessageCompleted += new EventHandler<ServiceReference1.GetMyMessageCompletedEventArgs>(s1c_GetMyMessageCompleted);
        }

        private void button1_Click(object sender, RoutedEventArgs e)
        {            
            s1c.GetMyMessageAsync();
        }

        void s1c_GetMyMessageCompleted(object sender, ServiceReference1.GetMyMessageCompletedEventArgs e)
        {
            MessageBox.Show(e.Result);
        }
        
    }
}
Note that all services in Silverlight are called asynchronously. Now if you run the solution, a message box will pop up when you click on the button.

2010-05-12 03-16-13 PM

So everything seems to be working on your local machine. For me the challenge was now getting it to work on my remote server. Which adds a few steps to the process. In addition, our server has shared hosting so that complicates the process even more.

Hosting the Solution

I now have a solution that works fine on my localhost, but when I upload it to my Shared Hosting Server I get an error with some of the details listed below…

Message: Unhandled Error in Silverlight Application An exception occurred during the operation, making the result invalid.  Check InnerException for exception details.   at System.ComponentModel.AsyncCompletedEventArgs.RaiseExceptionIfNecessary() 
   at SilverlightApplication6.ServiceReference1.GetMyMessageCompletedEventArgs.get_Result()
   at SilverlightApplication6.MainPage.s1c_GetMyMessageCompleted(Object sender, GetMyMessageCompletedEventArgs e) 
   at SilverlightApplication6.ServiceReference1.Service1Client.OnGetMyMessageCompleted(Object state) 

This is because my Service is not currently setup to run on shared hosting.

Firstly, I found a few blog posts on setting up services on shared hosting that were useful to read…

Installing a WCF service on Shared Hosting Revisted
WCF Services in a Shared Hosting Environment
WCF: This collection already contains an address with scheme http
WCF Service Hosting Common Issues
So I read the blogs and it all seems pretty simple… create a CustomHostFactory class under the .Web project. My class looked like this…

using System;
using System.ServiceModel.Activation;
using System.ServiceModel;
using System.Configuration;

namespace SilverlightApplication7.Web
{
    class CustomHostFactory : ServiceHostFactory
    {
        protected override ServiceHost
           CreateServiceHost(Type serviceType, Uri[] baseAddresses)
        {
            // Specify the exact URL of your web service
            var webServiceAddress = baseAddresses[0].ToString().Contains("localhost")
              ? baseAddresses[0]
              : new Uri("http://www.markpearl.co.za/Helloworld/Service1.svc");

            return (new CustomHost(serviceType, webServiceAddress));
        }
    }

    class CustomHost : ServiceHost
    {
        public CustomHost(Type serviceType,
           params Uri[] baseAddresses)
            : base(serviceType, baseAddresses)
        { }

        protected override void ApplyConfiguration()
        {
            base.ApplyConfiguration();
        }
    }
}
So… I upload everything to my site and immediately get an error when I click the button. Not the desired effect.

A bit more reading and head bashing and I decide the test the service separately by using directory browsing to get to the svc file.

I now get an error as follows…

Parser Error Message: The CLR Type 'SilverlightApplication7.Web.CustomHostFactory' could not be loaded during service compilation. Verify that this type is either defined in a source file located in the application's \App_Code directory, contained in a compiled assembly located in the application's \bin directory, or present in an assembly installed in the Global Assembly Cache. Note that the type name is case-sensitive and that the directories such as \App_Code and \bin must be located in the application's root directory and cannot be nested in subdirectories.

Some more reading around and I suspect it is because I don’t have a virtual directory setup. So I add a new virtual directory via my control panel with the following details…

2010-05-12 06-55-12 PM

Now when I put my url directed to the service it works, however when I click on my Silverlight project it still pulls up an error?

After a bit more investigating I discovered that it was the everything was working fine except that I was getting a cross domain policy error.

I believe cross domain policy errors are possibly a thing of the past with .Net 4 and shared hosting, but the following blog post that I did might help you if you ever get stuck.