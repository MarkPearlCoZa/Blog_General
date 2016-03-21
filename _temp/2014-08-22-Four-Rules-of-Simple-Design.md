---
layout: post
title: Four rules of simple design
tags: Concept
category: Design
---
#### General Notes ####

1. Tests Pass  
2. Express Intent  
3. No Duplication  
4. Small  

##### Tests Pass #####

- Focus on correctness and verification  
- Length of time it takes for a test to pass plays a significant factor in making changes  
- Tend towards automated tests  
- Tend towards making tests fast  

##### Express Intent #####

- It is easy for the names we give things to stray from what they represent  
- Pay attention to names and how code expresses itself  
- Size of structures and naming have a direct correlation  

##### No Duplication #####

- This is about knowledge duplication  
- Every piece of knowledge should have one and only one representation  

##### Small #####

- Do you have vestigal code that is no longer user?  
- Do you have any duplicate abstractions?  
- Have I extracted to far?  

------------------------------------------------------------------

#### Learnings from Code Retreats ####

##### Test Names should influence Objects APIs #####

- It is easy to forget that test names can stand in for documentation  
- Focussing on the symmetry between a good test name and the code under tests is a subtle design technique  
- Make sure you are actually testing what you say you are testing  

~~~
[TestFixture]
    class WorldTests
    {
        [Test]
        public void NewWorldIsEmpty()
        {
            var world = new World();
            Assert.That(world.LivingCellsCount(), Is.EqualTo(0));
        }

        [Test]
        public void CanAddACellToTheWorld()
        {
            var world = new World();
            world.SetLivingAt(1, 1);
            Assert.That(world.LivingCellsCount(), Is.EqualTo(1));
        }     
    }
~~~

If you look at the internals of the tests, they are not testing what the test name is suggesting. i.e. Empty World vs. LivingCellsCount. The second snippet gives a much better indication of the object api matching the tests.

~~~
    [TestFixture]
    class WorldTests
    {
        [Test]
        public void NewWorldIsEmpty()
        {
            var world = new World();
            Assert.True(world.IsEmpty());
        }

        [Test]
        public void CanAddACellToTheWorld()
        {
            var world = new World();
            Assert.False(world.CellAliveAt(1,1));

            world.SetLivingAt(1, 1);
            Assert.True(world.CellAliveAt(1,1));
        }
    }
~~~

##### Four stages of naming #####

- Names tend to go through four stages: nonsense, accurate, precise, meaningful.  
- Laziness or ignorance push us towards the left end of this spectrum, while with diligence we can move to the right. 
- Names further to the right of this spectrum provide more clarity.  

##### Duplication of Knowledge about Topology #####

- Good way to detect knowledge duplication is to ask "What happens if we want to change something?"  
- What effort is required and how many places will we need to look at and change?  
- Eliminating duplication relies on a strategy of reification (the act of taking a concept and making it real by extraction)  

~~~
  class World
    {
        public void SetLivingAt(int x, int y)
        {
            //..
        }

        public bool AliveAt(int x, int y)
        {
            //..
            return true;
        }
    }

    class DeadCell
    {
        public int X { get; set; }
        public int Y { get; set; }
    }

    class LivingCell
    {
        public int X { get; set; }
        public int Y { get; set; }
    }
~~~

What happens if we change the coordinate system?

~~~
   class CellLocation
    {
        public int X { get; set; }
        public int Y { get; set; }
    }

    class World
    {
        public void SetLivingAt(CellLocation location)
        {
            //..
        }

        public bool AliveAt(CellLocation location)
        {
            //..
            return true;
        }
    }

    class DeadCell
    {
        public CellLocation Location { get; set; }
    }

    class LivingCell
    {
        public CellLocation Location { get; set; }
    }
~~~


##### Behavior Attractors #####

- By aggresively eliminating knowledge of duplication through reification, we often find that we have built classes that naturally accept new behaviours that arise  
- They not only accept them, they attract them  
- Likewise, if we are working on a new behavior and are not sure where to place it, this may be an indication that we have a concept that is not expressed well in the system.

~~~
 class World
    {
        void SetLivingAt(int x, int y)
        {
            
        }

        bool AliveAt(int x, int y)
        {
            
        }
    }

    class Cell
    {
        public int X { get; set; }
        public int Y { get; set; }

        bool AliveInNextGeneration()
        {
            return true;
        }
    }
~~~

It is reasonable that we want to calculate the neighbors of a cell, where do we put it?  

~~~
IEnumerable<Tuple<int, int>> NeighborsOf(int x, int y)
        {
            //calculate the coordinates of neighbors
            throw new NotImplementedException();
        }
~~~

In the above scenario there isn't a clear place for it to go. A cell could know its neighbors, but the cell is also focussed on implementing the rules for evolving to the next generation. We could place it in the world class, but that smells too much like a god class. By eliminating knowledge of duplication we find that places appear that would be a good fit. In this instance the location class is a candidate.

~~~
class Location
    {
        public int X { get; set; }
        public int Y { get; set; }

        IEnumerable<Location> Neighbors()
        {
            //calculate the coordinates of neighbors
            throw new NotImplementedException();
        }
    }
~~~

##### Testing State vs Testing Behavior #####

- Focus on behavior is a common topic in software development conversations, but it isn't always clear how to do this  
- Building systems in a behavior focussed way is about only building things that are absolutely needed and only at the time they are needed  
- When wanting to add something new, ask what behavior in the system requires this new thing  

##### Don't have tests depend on previous tests #####

- Be careful that the context of a test isn't reliant on a different test to set the context.

~~~~
def test_an_empty_world_stays_empty_after_a_tick
	world = World.new
	next_world = world.tick
	assert_true next_world.empty?
end
~~~~

How do we know that a new world is an empty world?

Compare this too...

~~~
def test_an_empty_world_stays_empty_after_a_tick
	world = World.empty
	next_world = world.tick
	assert_true next_world.empty?
end
~~~

##### Naive Duplication #####

~~~
 public class Cell
    {
        public bool Alive { get; private set; }

        public int NumberOfNeighbors
        {
            get { return 2; }
        }

        public bool AliveInNextGeneration()
        {
            if (Alive)
            {
                return ((NumberOfNeighbors == 2) || (NumberOfNeighbors == 3));
            }

            return (NumberOfNeighbors == 3);
        }
    }
~~~

We might look at the above code and say we have duplication of 3, so we can remove that duplication.  

~~~
 public class CellAttempt
    {
        public bool Alive { get; private set; }

        private int NumberOfNeighbors()
        {
            return 2;
        }

        public bool AliveInNextGeneration()
        {
            return (Alive && NumberOfNeighbors() == 2) || (NumberOfNeighbors() == 3);
        }
    }
~~~

We have however produced naive duplication, while we have removed the 3, the 3 represents different things in each case. In the first case the 3 represents the concept of a stable state for an alive cell. In the second instance the 3 represents a genetically fertile neighborhood. This is only apparent if you look at the understanding of the domain. Restructurig the code to illustrate this concept is important for future use.

~~~
 public class CellAttempt
    {
        private int NumberOfNeighbors
        {
            get { return 2; }
        }

        public bool Alive { get; private set; }

        public bool AliveInNextGeneration()
        {
            if (Alive) return IsInStableState();
            return IsInGeneticallyFertileNeighborhood();
        }

        private bool IsInStableState()
        {
            return ((NumberOfNeighbors == 2) || (NumberOfNeighbors == 3));
        }

        private bool IsInGeneticallyFertileNeighborhood()
        {
            return (NumberOfNeighbors == 3);
        }
    }
~~~

------------------------------------------------------------------

#### References ####

[Iteration over the four rules of simple design](http://blog.thecodewhisperer.com/2013/12/07/putting-an-age-old-battle-to-rest/)  
[Four rules of simple design by Corey Haines](https://leanpub.com/4rulesofsimpledesign)  
[The four elements of simple design by JBrains](http://www.jbrains.ca/permalink/the-four-elements-of-simple-design)
[Duplication in software](http://www.justsoftwaresolutions.co.uk/design/duplication.html)
