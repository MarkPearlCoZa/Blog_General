---
layout: post
title: More QT4 (Assignment 3 Question 1)
tags: 
category: General
---
So, the last few days I have been finishing my summaries of my Programming Contemporary Concepts course. While it has been interesting being exposed to a new programming language, I found the actual course a bit framework specific, and not to contemporary at all. Needless to say, in the quest for the qualification I am going to put this aside and slog along.

Question 1 of Assignment 3 asks us to write a template Queue<T> class and client code to test it. I will be attempting it in QT4 using VS2008 as the IDE. Of course since this question focuses more on the code than anything visual I will be doing a console application.

Before I go into the actual code, lets first look at what a queue class needs to do…

I found this nice definition on cpluslus.com about queues.

queues are a type of container adaptors, specifically designed to operate in a FIFO context (first-in first-out), where elements are inserted into one end of the container and extracted from the other.

queues are implemented as containers adaptors, which are classes that use an encapsulated object of a specific container class as its underlying container, providing a specific set of member functions to access it elements. Elements are pushed into the "back" of the specific container and popped from its "front".

The underlying container may be one of the standard container class template or some other specifically designed container class. The only requirement is that it supports the following operations:

front()
back()
push_back()
pop_front()

I also found the following resource that also explained implementing a queue nicely…

So really, what we are wanting to achieve is a container class that handles four methods, front, back, push_back and pop_front.

Getting the Files
Okay, now that I know what they want me to do, I decided to first implement the example they put in the textbook of the stack. my thinking being a stack and queue will have almost an identical implementation/signature.

Problem 1… read through the example of the stack and it makes reference to qstd.h – I don’t have this… a bit of googling and I found the code samples on the web at the following address… but it turned out it wasn’t exactly what I was looking for…

More searching and discovered that the source is apparently on the Unisa disk.


 

For those that don’t have the disc, the files are compressed in a zip file above. But the files only included the source, and I needed the libraries. More searching and I located the libraries which are available for download below…


 

Now that I have all the necessary files I can actually consider coding a solution….

My Solution
I adjusted the stack class to be the queue class. Instead of just having a head, I had two variables, a front and a back variable. This was necessary so that I could track who was at the front and back of the queue.

The header looked as follows…

template<class T> class Queue 
{
 public:
    Queue(): m_Front(0), m_Tail(0), m_Count(0) {}
    ~Queue<T>() {delete m_Front; delete m_Tail;} ;
    void push(const T& t);
    T pop();    
    T front() const;
    T back() const;
    int count() const;

private:
    Node<T> *m_Front;
    Node<T> *m_Tail;
    int m_Count;
};

The actual implementation of push and pop were as follows…

//
// Pushes an item to the back of the queue
//
template <class T> void Queue<T>::push(const T& value) 
{
    Node<T> *newNode = new Node<T>(value);    
    
    if (m_Count == 0)
    {
        m_Front = newNode;    
        m_Tail = newNode;
    }
    else
    {
        m_Tail->setNext(newNode);        
        m_Tail = newNode;
    }
    
    ++m_Count;
}

///
/// Pops the item in the front of the queue off
///
template <class T>  T Queue<T>::pop() 
{
    Node<T> *popped = m_Front;
    if (m_Front != 0) 
    {        
        T retval = m_Front->getValue();                
        m_Front = m_Front->getNext();       
        popped->setNext(0);
        delete popped;
        --m_Count;
        return retval;        
    }
    return 0;
}
 

The only area where I got caught was on the delete command in the pop. I didn’t know that delete traverses the linked list and deletes all the connected nodes. Once I realized this I had to make sure that I set the next node to “0” on the node I was going to delete. Once that was realized the actual implementation was relatively simple.