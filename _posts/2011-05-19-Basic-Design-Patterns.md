---
layout: post
title: Basic Design Patterns
tags: 
category: General
---
I have been doing a rushed brush up on my contemporary concepts programming course – only to encounter more design patterns… so as revision I have listed some details below…

Today I am going to briefly cover 5 design patterns… namely:

Composite Pattern
Observer Pattern
Serializer Pattern
Monostate Pattern
Command Pattern
What are Design Patterns? (see wiki)
In programming we come across problems that are very similar, and certain approaches to solving these problems could be applied time and time again. Design patterns are an attempt to express the “best” approach so that it is reusable.

Composite Pattern
See Wiki Composite Pattern

The composite pattern is typically used when you want to treat a tree of objects as one object.

To build a tree of objects, you first need a composite class at the root of the tree and then add children to the composite class. A common scenario of implementing the composite pattern is for cad systems when a drawing can consist of a collection of sub items – each item needs to be drawn, but you would only want to trigger the draw state on the entire drawing…

This may all be a bit abstract to explain, but easier to look at the code to see what is happening…

With the c# implementation you will have a files…

Abstract class that would outline the common functions across each composite or leaf
An implementation of the composite class based on the abstract class
An implementation of the leaf class based on the abstract class
Abstract Class

    // the single interface for primitives & composite types.|
    public abstract class CompositeComponent
    {
        abstract public void AddChild(CompositeComponent c);
        abstract public void Draw();
    }
 

Composite Class

    public class Composite : CompositeComponent
    {
        private string _value = "";
        private List<CompositeComponent> _componentList = new List<CompositeComponent>();

        public Composite(string value)
        {
            _value = value;
        }

        public override void AddChild(CompositeComponent c)
        {
            _componentList.Add(c);
        }

        public override void Draw()
        {
            Console.WriteLine("Draw Composite : {0} ", _value);
            foreach (var itm in _componentList)
            {
                itm.Draw();
            }
        }
    }
Leaf Class

public class Leaf : CompositeComponent
    {
        private string _value = "";

        public Leaf(string value)
        {
            _value = value;
        }

        public override void AddChild(CompositeComponent c)
        {
            throw new Exception("Cannot add to a leaf");
        }

        public override void Draw()
        {
            Console.WriteLine("Draw Leaf : {0}", _value);
        }
    }
 

Example of an implementation

    class Program
    {
        static void Main(string[] args)
        {
            // Creating a TREE structure.
            Composite root = new Composite("Root");
            Composite com1 = new Composite("Composite 1");
            Leaf leaf1 = new Leaf("Leaf 1");
            Leaf leaf2 = new Leaf("Leaf 2");
            Leaf leaf3 = new Leaf("Leaf 3");
            
            // Add two leafs to composite1
            com1.AddChild(leaf1);
            com1.AddChild(leaf2);

            Console.WriteLine("Example 1 - Draw Composite");
            com1.Draw();

            root.AddChild(leaf3);
            root.AddChild(com1);            
            
            // Single method for both types.
            Console.WriteLine("\n \nExample 2 - Draw Root");
            root.Draw();
            Console.ReadLine();
        }
    }
 

Output of Example

Composite

QT’s specific implementation of the composite pattern

In QT, the QObject class represents the application of a simplified form of the composite pattern, however unlike my representation in the code below, in QT they have implemented the component and the composite into the same class.

To make one object the child of another with the QTObject you simply call the setParent. This is where it varies form the classic composite pattern as it does not have a set child method.

Monostate Pattern
Sometimes you may have situations where you want to be able to access across the application, for instance a General Settings object. In the past I have used the singleton pattern to apply this. The one downside of a singleton class is that if at a later stage you want to change the object so that it is a normal object, you need to go to every point where you referenced the singleton and change it to a normal object.

(Drum Roll) enter the Monostate Pattern (End Drum Roll)

The Monostate pattern tries to accomplish something similar to a singleton pattern, but in a very different way. It makes a object look to the outside user as if it is a normal class, however whenever you access data members of the class you are in fact accessing the same data. The simplest way to achieve the monostate pattern is to make all the data members of the class static. Whether this is a good thing or a bad thing is probably up to the beholder, but it is interesting to have a quick look at how this is implemented…

 

    public class Monostate 
    { 
        private static string _dataItem;         //static data

        public string DataItem 
        { 
            get { return _dataItem;  } 
            set { _dataItem = value; } 
        }         
    }
Looking at using this class we can see how the fact that it is accessing a static instance of the object is hidden…

        static void Main(string[] args)
        {
            Monostate myobj1 = new Monostate();
            myobj1.DataItem = "123";

            Monostate myobj2 = new Monostate();
            myobj2.DataItem = "456";

            Console.WriteLine("Object 1 : {0}", myobj1.DataItem);
            Console.WriteLine("Object 2 : {0}", myobj2.DataItem);
            Console.ReadLine();
        }
 

This would give you the following output…

Monostate

Which from what you can see myobj1 DataItem has changed even though it was not apparent when looking at the code of the main class.

 

Observer Pattern
See Wiki on Observer Pattern

The observer pattern is useful when you want a number of objects to view/react to the state of a particular object without the object having to specifically tell them to react. In the classic observer pattern you will have two abstract classes – one for the subject and one for the observer. You then can have objects that implement the abstract observer or abstract subject…

Lets have a look at an example abstract subject and observer class…

    abstract class Subject
    {
        private List<Observer> _observers = new List<Observer>();

        public void Attach(Observer observer)
        {
            _observers.Add(observer);
        }

        public void Detach(Observer observer)
        {
            _observers.Remove(observer);
        }

        public void Notify()
        {
            foreach (Observer o in _observers)
            {
                o.Update();
            }
        }
    }
    abstract class Observer
    {
        public abstract void Update();
    }
 

You can now have concrete implementation of each class as illustrated below…

    /// <summary>
    /// The 'ConcreteSubject' class
    /// </summary>
    class ConcreteSubject : Subject
    {
        private string _subjectState;

        // Gets or sets subject state
        public string SubjectState
        {
            get { return _subjectState; }
            set { _subjectState = value; }
        }
    }
   

    /// <summary>
    /// The 'ConcreteObserver' class
    /// </summary>
    class ConcreteObserver : Observer
    {

        private string _name;
        private string _observerState;        

        // Constructor
        public ConcreteObserver(ConcreteSubject subject, string name)
        {
            this.Subject = subject;
            this._name = name;
        }

        public override void Update()
        {
            _observerState = Subject.SubjectState;
            Console.WriteLine("Observer {0}'s new state is {1}", _name, _observerState);
        }

        // Gets or sets subject
        public ConcreteSubject Subject { get; set; }       
    }
 
An implementation of the these classes is illustrated below…

        static void Main(string[] args)
        {            
            // Configure Observer pattern
            ConcreteSubject s = new ConcreteSubject();

            ConcreteObserver ObserverObject1 = new ConcreteObserver(s, "Object1");
            ConcreteObserver ObserverObject2 = new ConcreteObserver(s, "Object2");
            ConcreteObserver ObserverObject3 = new ConcreteObserver(s, "Object3");

            s.Attach(ObserverObject1);
            s.Attach(ObserverObject2);
            s.Attach(ObserverObject3);

            // Change subject and notify observers
            s.SubjectState = "ABC";
            s.Notify();

            //Detach one observer
            s.Detach(ObserverObject2);                        

            // Change subject and notify observers
            s.SubjectState = "CDE";
            s.Notify();

            // Wait for user
            Console.ReadKey(); ;
        }
 
Which would give the following output…

Observer

Just to keep in mind that the observer pattern is very similar to the event aggregator pattern used commonly in MVVM application.

QT’s specific implementation of the observer pattern

The QObject class represents the application of a simplified observer pattern in its use of signals and slots. QObject represents the Subject, Observer, ConcreteSubject and ConcreteObserver classes all rolled into one.

QObject has a static member called connect() which is used to connect a subject to an observer. It also allows you to specify which change of state (the signal) should cause which update (the slot). Numerous observers can be connected to a single subject, and one observer can be connected to numerous subjects.

Serializer Pattern
Due to time constraints I am not going to go into to much detail on this pattern, other than a brief explanation…

The serializer pattern is such that if you want to save/load the state of an object to the screen or file, instead of implementing the read and write methods inside the class, instead you implement a separate reader and writer class that accepts the targeted class as a parameter.

Command Pattern
See Wiki on Command Pattern

Again a fairly common pattern, but one I am not going to go into to much detail in this post.

QT’s specific implementation of the command pattern

The closest we get in QT to the classic command pattern is with the QAction object. All events are represented by objects of type QAction. The rest of the classes in the classic Command pattern do not have direct equivalents in QT.