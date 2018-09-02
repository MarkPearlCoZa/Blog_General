---
layout: post
title: QT4, C++ and learning the basics… again (COS2144 Assignment 2, Question 1)
tags: 
category: University
---
If anyone has been following my blogs lately, they would have noticed that they just had random rumblings of book summaries for my CS degree. This is actually the first semester where I am battling to keep up with the level of work – possibly because up to now the courses have been rather easy to complete the class work (multiple choice), and possibly because work work has gotten extremely busy which has left me with only one day a week (Saturday) to dedicate to learning and doing my assignments. That being said I thought I would document one of my assignments – purely so that I can come back to this blog and follow my thought pattern.

The Question…

Implement the Account and JointAccount classes given in Examples 6.20, 6.21 and 6.22, except that you must replace the type of the m_Owner data member in the Account class, and the m_JointOwner data member in the JointAccount class from string to Client. 

The Client class should have five data members of type QString, namely m_FirstName, m_LastName, m_Address1, m_Address2 and m_PostalCode. It should have a constructor (to initialise all data members) and a toString member function.

Then implement a class called  AccountList that inherits from  QList. It should store (pointers to) Account objects. It should have the following member functions: 

QString toString();
Account * findAccount(unsigned accNum);
bool addAccount(Account * acc);
bool removeAccount(unsigned accNum); 
Make sure that  addAccount() does not allow the same account to be added more than once (although it should allow more than one account to be added for the same client).

Write a main program to test these classes. It should create a number of  Account and JointAccount objects and add them to an instance of AccountList, and test all the other member functions of the AccountList class.
Submit code of all the classes  that you have written (or adapted), as well as the main program.
Submit a copy of the output produced by a typical test run of the program.
Note that your program should be a console application, not a GUI app.

My Workings…

Setters & Getters

So the first section is fairly easy – the classes are outlined in the book. I then had to create the Client class.. again nothing to complicated. While creating the class I came along the question of properties… in dynamic languages like c# to access private data one would create a property. After initially searching about the topic I discovered that c++ does not have this sort of functionality built in (or it was apparent to me). Instead they suggest using getters & setters, which is based on the same concept, but is a more raw implementation. With implementing the setters & getters in my client class the class header looked like the following…

class Client 
{
public:
    Client();
    Client(QString firstname, QString lastname, QString address1, QString address2, QString postalcode);

    // Setters
    void setFirstName(QString newVal);
    void setLastName(QString newVal);
    void setAddress1(QString newVal);
    void setAddress2(QString newVal);
    void setPostalCode(QString newVal);    

    // Getters
    QString getFirstName() const;
    QString getLastName() const;
    QString getAddress1() const;
    QString getAddress2() const;
    QString getPostalCode() const;


    QString toString() const;
    ~Client();

private:
    QString  m_FirstName;
    QString  m_LastName;
    QString  m_Address1;
    QString  m_Address2;
    QString  m_PostalCode;
};
 

I then had a relook at the problem, and for the client class I will probably not need setters & getters for each private member, however I will need getters for the account class so that the joint account can create an instance of the account object… If we have a look at the Joint Account implementation I needed to expand the account class to allow for the following…

JointAccount::JointAccount(const Account & acct, Client jowner) : Account(acct->GetAccountNumber(),acct->GetBalance(),acct->GetOwner())
{
}
 

This left me with an account class that looked like this

class Account 
{
    
public:    
    Account(unsigned acctNum, double balance, Client & owner);        
    virtual ~Account();        

    //Getters
    unsigned GetAccountNumber();
    double GetBalance();
    Client GetOwner();

    // Methods
    QString toString() const;

private:
    unsigned m_AcctNum;
    double m_Balance;
    Client m_Owner;
};

That all looked fine, until I reread the code sample and realized that in fact the getter were not necessary… if I looked back at the joint account class I should have done the following…

JointAccount::JointAccount(const Account & acct, Client jowner) : Account(acct)
{
    m_JointOwner = jowner;
}

Which compiled and achieved what I wanted… so I removed the getters again… I now began to look at implementing methods that would assist in testing my classes. I decided that I would override or create the trostring method for each class, which would allow me to visibly test each object and its member variables status. To implement the tostring in the Account & Client object it was a fairly simple process of adding the tostring method to each class.

QString Account::toString() const
{
    Helper h;
    return "Acc : " + h.QStringFromDouble(m_AcctNum) + " , Balance : " + h.QStringFromDouble(m_Balance) + " , Client : " + m_Owner.toString();    
}

When I came across the jointacount class I hit a bit of a snag – I wanted to override the account classes tostring method (which was inherited by the jointaccount class) but I couldn’t figure out the correct syntax to access the account class members from the jointclass… i.e. I wanted to do the following…

QString JointAccount::toString() const
{
    Helper h;        
    return "Joint Account " + m_JointOwner.toString() + ", " + // Account Class ToString
}

Eventually after spinning the brain wheels a bit I figured out what I wanted to do was access a base class from a derived class… A bit of searching stack overflow brouight me to a post that was similar to what I wanted to achieve.. so with a little bit of playing I got the following to work…

QString JointAccount::toString() const
{
    return "Joint Account owner " + m_JointOwner.toString() + " linked to " + this->Account::toString();
}
 

Now that I got my owner, account & joint account classes working, I needed to tackle the account list. I was working in VS2008 with WT4 and I implemented the account list class as follows…

 

#include <QList>
#include "Account.h"

class AccountList : public QList<Account*>
{

public:
    AccountList();
    ~AccountList();
    
    Account * findAccount(unsigned accNum);
    bool addAccount(Account * acc);
    bool removeAccount(unsigned accNum);

    QString toString() const;

private:    
};

For some reason though intellisense was not showing the inherited classes member methods, which lead me to initially think that the methods were not there…

i.e. in the image below intellisense is not showing the insert method which is inherited from QList, however it definitely exists…

2010-08-28 11-49-41 AM

 

Once I had discovered this, then implementing the AccountList class was a snap since I just referenced the methods from the QList class.

Finally, the requested that I make a test function to test all the classes. To make the testing easier I expanded the toString methods to all the classes so I could see the output easily… Initially my test function gave out some the correct output, but it looked a bit jumbled (see image below)

2010-08-28 12-13-46 PM

 

I refactored the tostrings so that it would all fit on one line…

2010-08-28 12-24-27 PM

If we examine the test function below it seems to comply with the output…

void Test()
{
    // Client Object Testing
    qDebug() << "Test Client Testing";
    
    Client *myClient1 = new Client("myFN1","myLN1","myA1-1","myA2-1","myP-1");
    Client *myClient2 = new Client("myFN2","myLN2","myA1-2","myA2-2","myP-2");
    Client *myClient3 = new Client("myFN3","myLN3","myA1-3","myA2-3","myP-3");

    qDebug() << "C1 Created..." << myClient1->toString() << endl
             << "C2 Created..." << myClient2->toString() << endl
             << "C3 Created..." << myClient3->toString() << endl;

    // Account Object Testing
    qDebug() << "Test Account Testing";
    
    Account *myAccount1 = new Account(1,1,*myClient1);
    Account *myAccount2 = new Account(2,2,*myClient2);
    Account *myAccount3 = new Account(3,3,*myClient3);
    
    qDebug() << "A1 created..."  << myAccount1->toString() << endl
             << "A2 created..."  << myAccount2->toString() << endl
             << "A3 created..."  << myAccount3->toString() << endl
             << endl;

    // Joint Account Object Testing
    qDebug() << "Test Joint Account Testing";
    
    JointAccount *myJointAccount1 = new JointAccount(22,1,*myClient1,*myClient2);    
    JointAccount *myJointAccount2 = new JointAccount(23,1,*myClient3,*myClient1);    

    qDebug() << "JA1 created..." << myJointAccount1->toString() << endl 
             << endl
             << "JA2 created..." << myJointAccount2->toString() << endl
             << endl;
    
    // Account List Testing
    qDebug() << "Test List Accounts";
    AccountList *myAccountList = new AccountList();

    myAccountList->addAccount(myAccount1);    
    myAccountList->addAccount(myAccount2);
    myAccountList->addAccount(myAccount2);        
    myAccountList->addAccount(myAccount3);        
    myAccountList->removeAccount(3);    
    qDebug()<< "Account List : " << myAccountList->toString();
}
 