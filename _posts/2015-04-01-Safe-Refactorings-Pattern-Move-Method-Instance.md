---
layout: post
title: Safe Refactoring Pattern - Move Instance Method
tags: Refactoring
category: General
---
#### Goal ####

Move an instance method from one class to another.

#### Scenario ####

You have a class with an instance method, you've identified that this method fits better in another class and you want to move it.Instead of doing this use the 'Move Instance Method Pattern' to safely move an instance method. The steps are...

#### Unsafe Approach ####

- Cut method you want to move.  
- Paste it in the new class.
- Use the compiler to detect build failures where the method on the old class is being used.  
- Manually make a new instance of the class for each usage and reference the new location of the method.

#### Safe Approach ####

- Make the method you want to move static.  
- Move the static method to the class you want it in.  
- Pass an instance of the new class into each place where the method is being used.
- Make the moved method unstatic. 

#### Walk Through ####

<iframe width="560" height="315" src="https://www.youtube.com/embed/uc02cGvCwVc" frameborder="0" allowfullscreen></iframe>

#### Example Beginning State ####
~~~
	public class Class1
	{
		public void MethodA()
		{
			//Do MethodA
		}

		public void MethodB()
		{
			//Do MethodB
		}
	}

	public class Class2
	{
		// *** You want to move the instance method here ***
	}

	public class MoveInstanceMethodExample
	{
		public void ExampleMethod()
		{
			var class1 = new Class1();
			class1.MethodA();
			class1.MethodB();
		}
	}
~~~

#### Example End State ####
~~~
	public class Class1
	{
		public void MethodA()
		{
			//Do Method A
		}
	}

	public class Class2
	{
		public void MethodB()
		{
			//Do Method B
		}
	}

	public class MoveInstanceMethodExample
	{
		public void ExampleMethod()
		{
			var class1 = new Class1();
			class1.MethodA();

			var class2 = new Class2();
			class2.MethodB();
		}
	}
~~~


#### Notes ####

- This refactoring was done with ReSharper 9, I cannot guarentee previous or future version support. 

