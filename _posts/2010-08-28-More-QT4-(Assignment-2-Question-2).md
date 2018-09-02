---
layout: post
title: More QT4 (Assignment 2 Question 2)
tags: 
category: University
---
So the first question took sometime, partly because I was getting used to c++ again, and partly because of the way VS2008 works with QT. Anyhow, question 2 was dramatically easier.

The Question…

Write an application,similar to the one in Section 9.3,but that has four buttons.

The first one, labelled Advice,should be connected to a slot that randomly selects a piece of text (such as a fortune cookie) and displays it in the 
QTextEdit window.
The second one, labelled Weather,randomly selects a sentence about the weather and displays it in the QTextEdit window.
The third one, labelled Next Meeting, pops up a message dialog with a randomly generated (fictitious) meeting time and descriptive message in it.
The fourth one, labeled Quit,terminates the program.Use signals and slots to connect the button clicks with the appropriate functions.
My Workings…

Initially I created a QTApplication with a window as per VS2008 templates – this however was not what was being illustrated in section 9.3, the difference being in section 9.3 the window is generated in code, while as the default template in VS2008 has a window editor so I went back to the book and copied the example code.

The example code was relatively simple, two buttons and when you clicked on the shout button a popup dialog would appear with shout. After having a look at the example code the only real area of confusion was how slots & signals worked. The following reference was useful...

A little bit of confusion from the textbook was when they used setGui. Initially I thought this was built into the libraries, but it turned out to be user defined method. With that in mind I was able to implement a new setGui that had the layout as requested…

QWidget* setGui(QWidget *box)
{
    QLayout* layout = new QVBoxLayout;
    box->setLayout(layout);

    // Textbox     
    QTextEdit *te = new QTextEdit;
    layout->addWidget(te);
    te->setHtml("");
    
    // Buttons
    QPushButton *adviceButton = new QPushButton("Advice");
    QPushButton *weatherButton = new QPushButton("Weather");
    QPushButton *nextmeetingButton = new QPushButton("Next Meeting");
    QPushButton *quitButton = new QPushButton("Quit");        
    
    layout->addWidget(adviceButton);    
    layout->addWidget(weatherButton);    
    layout->addWidget(nextmeetingButton);    
    layout->addWidget(quitButton);    
    
    //Tie buttons to slots    
    Messager *mymsg = new Messager(te, box);
    qApp->connect(adviceButton, SIGNAL(clicked()), mymsg, SLOT(advice()));
    qApp->connect(weatherButton, SIGNAL(clicked()), mymsg, SLOT(weather()));
    qApp->connect(nextmeetingButton, SIGNAL(clicked()), mymsg, SLOT(nextmeeting()));

    QObject::connect(quitButton, SIGNAL(clicked()), qApp, SLOT(quit()));    
    return box;
}

This gave the following layout….

2010-08-28 03-07-05 PM 

I then refactored the messager class which left me with the following header outline…

#include <QObject>
#include <QtGui>
#include <QWidget>
#include <QString>
#include <QList>
#include <stdlib.h>
#include <QErrorMessage>

class Messager : public QObject
{
    Q_OBJECT

public:
    Messager(QTextEdit* te, QWidget* parent=0);    
    ~Messager();

public slots:    
    void advice();
    void weather();
    void nextmeeting();

private:
    QWidget* m_Parent;
    QErrorMessage* message;
    QTextEdit* m_te;
    QList<QString> myWeatherList;
    QList<QString> myAdviceList;
    QList<QString> myMeetingList;
};
 

I decided to make the random messages be contained within the messager class. I guess I could have put these outside the class, but I couldnt see any reason for example purposes to do so.

This left me with the following messager implementation…

#include "messager.h"

//================================================
// Constructors
//================================================

Messager::Messager(QTextEdit* te, QWidget* parent) : m_Parent(parent)
{
    m_te = te;
    message = new QErrorMessage(parent);        
    
    myWeatherList
        << "Sunny Today?" 
        << "Gona Rain!"
        << "Cloudy and Cold...";
    
    myAdviceList 
        << "I think its time to close the program" 
        << "Maybe its time to check the weather"
        << "Time to stop working"
        << "How about some random advice";        

    myMeetingList
        << "Time to Program"
        << "Time to Study"
        << "Time to Work";
}

Messager::~Messager(){}

//================================================
// Methods
//================================================

void Messager::advice()
{            
    m_te->setHtml(myAdviceList[rand() % myAdviceList.size()]);
}

void Messager::weather()
{                        
    m_te->setHtml(myWeatherList[rand() % myWeatherList.size()]);
}


void Messager::nextmeeting()
{    
    int h = (rand() % 24);
    int m = (rand() % 60);    

    message->showMessage(
        "Meeting at " + 
        QString::number(h) + ":" + QString::number(m) 
        + " - " + myMeetingList[rand() % myMeetingList.size()]);
}

Again nothing to complicated. To areas that were a bit tricky was converting from an int to QString. Eventually I discovered that QString has a number method that does this conversion as a typical type cast was converting to a character equivalent.

Also, initially I was randomizing the seed generator every time I was generating a random number – this was calling a bug where the random number would always follow the same pattern because the ransom seed generator should only be called once in a project. When I moved this to the main function everything worked great…

int main(int argc, char *argv[])
{
    srand (time(NULL));    
    QApplication myapp(argc, argv);
    QWidget rootWidget;
    setGui(&rootWidget);    
    rootWidget.show();    
    return myapp.exec();
}