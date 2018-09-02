---
layout: post
title: Linked Lists in C++
tags: 
category: General
---
General

Basically, a linked list is a collection of nodes. Each node in the list has two components – a components to store information about that node (i.e. data) and a component to store the next “linked” node. The last node in a linked list indicates that it does not have a “linked” node – usually by a null reference. The address of the first node is stored in a separate location, called the head or first.

 

singlelinkedlist

The code snippet below shows a basic structure of a node declaration in c++.

~~~
struct nodeType
{
    int data;
    nodeType *link;
};
~~~
 

The variable declaration is as follows…

nodeType *head;
 

Basic Operations of a Linked List

There are a few basic operations that are typically needed with a linked list

Search a list to determine whether a particular item is in the list
Insert an item in the list
Delete an item from the list
Traversing/Searching a List

To traverse a linked list you need some way to move around the list. The *head is a pointer in the list, but you cannot use it to traverse the list because then you would loose a reference to the beginning of the list.

Typically to traverse the list, you will need to declare another pointer that follows the same declaration as head, but that is not critical if you change where it’s pointing to…

~~~
current = head;
while (current != NULL)
{
    cout << current->data << " ";
    current = current->link;
}
~~~
 

Item Insertion and Deletion

To insert a new node into a linked list, you need to do the following:

Create a new node
Determine the position in the list that you want to insert it and assign it to current
Make the new node is point to the same link that current is pointing to
Make current now point to the new node
In code, assuming current was at the correct position, then it would look something like this…

~~~
nodeType *newNode;

newNode = new nodeType;
newNode->data = 123;
newNode->link = current->link;
current->link = newNode;
~~~
 

To delete a node from a linked list, you need to do the following:

Determine the node that you want to remove and point current to the node prior to that node
Create a pointer to point to the node you want to delete (i.e. *p)
Make current’s link now point to p’s link
delete p from memory
In code, assuming current was at the correct position, then it would look something like this…

~~~
deleteNode = new nodeType;
deleteNode = current->link;
current->link = deleteNode->link;
delete deleteNode;
~~~

Building a Linked List

There are two main ways to build a linked list, forward and backward.

I find the best way to explain this approach is code…. below if the forward approach, meaning the node is inserted forwards – i.e. at the back of the list…

~~~
int main()
{
    //
    // Init the list
    //
    nodeType *first;
    nodeType *last;
    nodeType *newNode;
    int num;

    first = NULL;
    last = NULL;

    //
    // Build the list the forward approach
    //
    for (int i=0; i<3; i++)
    {
        cout << "Enter number :";
        cin >> num;
        newNode = new nodeType;         // Create the new node
        newNode->data = num;            // and assign its data value
        newNode->link = NULL;           // make its link point to nothing
        if (first == NULL)              // If there is nothing in the list, then make the 
        {                               // newNode the first item and the last item
            first = newNode;
            last = newNode;
        }
        else                            // Else if first already has a value
        {                               // make the last item link to the newNode
            last->link = newNode;       // and make newNode the last item
            last = newNode;
        }
    }
    //
    // Display the list
    //
    DisplayList(first);
    system("PAUSE");
    return(0);
}
~~~
 

If you look at the forward approach, you need two pointers to maintain the list – first & last. This is because you don’t want to traverse the list each time you want to add something. The backward way of building a list in my opinion is easier to read and code since you only need to worry about the head of the list. The code implementation is listed below…

~~~
//
// Init the list
//
nodeType *head;    
nodeType *newNode;
int num;
head = NULL;    

//
// Build the list using the backward approach
//
for (int i=0; i<3; i++)
{
    cout << "Enter number :";
    cin >> num;
    newNode = new nodeType;         // Create the new node
    newNode->data = num;            // and assign its data value
    newNode->link = head;           // make its link point to the front of the list
    head = newNode;                 // make the head now be the newNode
}
~~~

Sorted & Unsorted Linked Lists

Typically there are two types of linked lists, those that are sorted and those that are unsorted.

The advantages of knowing that a collection of data is sorted when performing searches greatly reduces the complexity of the search algorithms as well as improving the searches performance.

Typically to maintain a sorted listed requires adjusting the insert method so that when a list is being built, the order is maintained.

Doubly Linked Lists

A doubly linked list is a linked list that every node has its “next” and “previous” node stored.

The advantages of a doubly linked list are that it can be traversed in any direction, which can be beneficial when performing iterations on the list.

The basic structure of a doublelinkedlist node is shown below…

~~~
struct doublenodeType
{
    int data;
    nodeType *next;
    nodeType *previous;
};
~~~
 

Circular Linked Lists

As the name suggest, a circular linked lists is one where the first node points to the last node of the list.