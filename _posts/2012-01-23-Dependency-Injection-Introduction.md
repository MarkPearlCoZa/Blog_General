---
layout: post
title: Dependency Injection Introduction
tags: 
category: General
---
I recently was going over a great book called “Dependency Injection in .Net” by Mark Seeman. So far I have really enjoyed the book and would recommend anyone looking to get into DI to give it a read. Today I thought I would blog about the first example Mark gives in his book to illustrate some of the benefits that DI provides.

The ones he lists are

Late binding
Extensibility
Parallel Development
Maintainability
Testability
To illustrate some of these benefits he gives a HelloWorld example using DI that illustrates some of the basic principles. It goes something like this…

    class Program
    {
        static void Main(string[] args)
        {
            var writer = new ConsoleMessageWriter();
            var salutation = new Salutation(writer);
            salutation.Exclaim();
            Console.ReadLine();
        }        
    }

    public interface IMessageWriter
    {
        void Write(string message);
    }        

    public class ConsoleMessageWriter : IMessageWriter
    {
        public void Write(string message)
        {       
            Console.WriteLine(message);
        }
    }

    public class Salutation
    {
        private readonly IMessageWriter _writer;

        public Salutation(IMessageWriter writer)
        {
            _writer = writer;
        }

        public void Exclaim()
        {
            _writer.Write("Hello World");
        }
    }
 

If you had asked me a few years ago if I had thought this was a good approach to solving the HelloWorld problem I would have resounded “No”. How could the above be better than the following….

    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World");            
            Console.ReadLine();
        }        
    }
 
Today, my mind-set has changed because of the pain of past programs. So often we can look at a small snippet of code and make judgements when we need to keep in mind that we will most probably be implementing these patterns in projects with hundreds of thousands of lines of code and in projects that we have tests that we don’t want to break and that’s where the first solution outshines the latter.

Let’s see if the first example achieves some of the outcomes that were listed as benefits of DI. Could I test the first solution easily? Yes… We could write something like the following using NUnit and RhinoMocks…

    [TestFixture]
    public class SalutationTests
    {
        [Test]
        public void ExclaimWillWriteCorrectMessageToMessageWriter()
        {
            var writerMock = MockRepository.GenerateMock<IMessageWriter>();
            var sut = new Salutation(writerMock);
            sut.Exclaim();            
            writerMock.AssertWasCalled(x => x.Write("Hello World"));            
        }        
    }
 

This would test the existing code fine. Let’s say we then wanted to extend the original solution so that we had a secure message writer. We could write a class like the following…

    public class SecureMessageWriter : IMessageWriter
    {
        private readonly IMessageWriter _writer;
        private readonly string _secretPassword;        

        public SecureMessageWriter(IMessageWriter writer, string secretPassword)
        {
            _writer = writer;
            _secretPassword = secretPassword;
        }

        public void Write(string message)
        {
            if (_secretPassword == "Mark")
            {
                _writer.Write(message);
            }
            else
            {
                _writer.Write("Unauthenticated");
            }
        }
    }
 

And then extend our implementation of the program as follows…

    class Program
    {
        static void Main(string[] args)
        {
            var writer = new SecureMessageWriter(new ConsoleMessageWriter(), "Mark");
            var salutation = new Salutation(writer);
            salutation.Exclaim();
            Console.ReadLine();
        }   
    }
 

Our application has now been successfully extended and yet we did very little code change. In addition, our existing tests did not break and we would just need add tests for the extended functionality.

Would this approach allow parallel development? Well, I am in two camps on parallel development but with some planning ahead of time it would allow for it as you would simply need to decide on the interface signature and could then have teams develop different sections programming to that interface.

So,this was really just a quick intro to some of the basic concepts of DI that Mark introduces very successfully in his book. I am hoping to blog about this further as I continue through the book to list some of the more complex implementations of containers.