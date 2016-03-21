---
layout: post
title: OO Constructors
tags: OO
category: Programming
---
#### Named Constructors ####

~~~
public class Game
{
	//
	// Constructor that doesn't give any context
	//
	public Game()
	{
	}

	//
	// Name Constructor
	//
	public static Game NewIndieGame()
	{
		Game newGame = new Game();
		//... set state
	}
}
~~~

#### Summary of a Constructors Purpose ####
- I want constructors only to initialise new instances to a rational state, so I move more interesting code into named constructors.  
- Now that I have to give this construction behavior a name, cohesion and dependency problems become explicit and obvious.  
- Now that I have identified explicit, obvious design problems, I can decide how and when to improve the design.  

#### References ####
[Bloated Constructors](http://www.daedtech.com/beware-the-bloated-constructor)
