---
layout: post
title: Sorting Algorithms
tags: 
category: General
---
General

Every time I go back to university I find myself wading through sorting algorithms and their implementation in C++. Up to now I haven’t really appreciated their true value. However as I discovered this last week with Dictionaries in C# – having a knowledge of some basic programming principles can greatly improve the performance of a system and make one think twice about how to tackle a problem.

I’m going to cover briefly in this post the following:

Selection Sort
Insertion Sort
Shellsort
Quicksort
Mergesort
Heapsort (not complete)
Selection Sort

Array based selection sort is a simple approach to sorting an unsorted array. Simply put, it repeats two basic steps to achieve a sorted collection. It starts with a collection of data and repeatedly parses it, each time sorting out one element and reducing the size of the next iteration of parsed data by one.

So the first iteration would go something like this…

Go through the entire array of data and find the lowest value
Place the value at the front of the array
The second iteration would go something like this…

Go through the array from position two (position one has already been sorted with the smallest value) and find the next lowest value in the array.
Place the value at the second position in the array
This process would be completed until the entire array had been sorted.

A positive about selection sort is that it does not make many item movements. In fact, in a worst case scenario every items is only moved once.

Selection sort is however a comparison intensive sort. If you had 10 items in a collection, just to parse the collection you would have 10+9+8+7+6+5+4+3+2=54 comparisons to sort regardless of how sorted the collection was to start with.

If you think about it, if you applied selection sort to a collection already sorted, you would still perform relatively the same number of iterations as if it was not sorted at all. Many of the following algorithms try and reduce the number of comparisons if the list is already sorted – leaving one with a best case and worst case scenario for comparisons. Likewise different approaches have different levels of item movement. Depending on what is more expensive, one may give priority to one approach compared to another based on what is more expensive, a comparison or a item move.

Insertion Sort
Insertion sort tries to reduce the number of key comparisons it performs compared to selection sort by not “doing anything” if things are sorted.

Assume you had an collection of numbers in the following order…

10 18 25 30 23 17 45 35

There are 8 elements in the list. If we were to start at the front of the list – 10 18 25 & 30 are already sorted. Element 5 (23) however is smaller than element 4 (30) and so needs to be repositioned. We do this by copying the value at element 5 to a temporary holder, and then begin shifting the elements before it up one. So…

Element 5 would be copied to a temporary holder	10 18 25 30 23 17 45 35 – T 23
Element 4 would shift to Element 5	10 18 25 30 30 17 45 35 – T 23
Element 3 would shift to Element 4	10 18 25 25 30 17 45 35 – T 23
Element 2 (18) is smaller than the temporary holder so we put the temporary holder value into Element 3.	10 18 23 25 30 17 45 35 – T 23
 

We now have a sorted list up to element 6. And so we would repeat the same process by moving element 6 to a temporary value and then shifting everything up by one from element 2 to element 5.

As you can see, one major setback for this technique is the shifting values up one – this is because up to now we have been considering the collection to be an array. If however the collection was a linked list, we would not need to shift values up, but merely remove the link from the unsorted value and “reinsert” it in a sorted position. Which would reduce the number of transactions performed on the collection.

So.. Insertion sort seems to perform better than selection sort – however an implementation is slightly more complicated. This is typical with most sorting algorithms – generally, greater performance leads to greater complexity.

Also, insertion sort performs better if a collection of data is already sorted. If for instance you were handed a sorted collection of size n, then only n number of comparisons would need to be performed to verify that it is sorted.

It’s important to note that insertion sort (array based) performs a number item moves – every time an item is “out of place” several items before it get shifted up.

Shellsort – Diminishing Increment Sort
So up to now we have covered Selection Sort & Insertion Sort. Selection Sort makes many comparisons and insertion sort (with an array) has the potential of making many item movements.

Shellsort is an approach that takes the normal insertion sort and tries to reduce the number of item movements.

In Shellsort, elements in a collection are viewed as sub-collections of a particular size. Each sub-collection is sorted so that the elements that are far apart move closer to their final position.

Suppose we had a collection of 15 elements…

10 20 15 45 36 48 7 60 18 50 2 19 43 30 55

First we may view the collection as 7 sub-collections and sort each sublist, lets say at intervals of 7

10 60 55 – 20 18 – 15 50 – 45 2 – 36 19 – 48 43 – 7 30

10 55 60 – 18 20 – 15 50 – 2 45 – 19 36 – 43 48 – 7 30 (Sorted)

We then sort each sublist at a smaller inter – lets say 4

10 55 60 18 – 20 15 50 2 – 45 19 36 43 – 48 7 30

10 18 55 60 – 2 15 20 50 – 19 36 43 45 – 7 30 48 (Sorted)

We then sort elements at a distance of 1 (i.e. we apply a normal insertion sort)

10 18 55 60 2 15 20 50 19 36 43 45 7 30 48

2 7 10 15 18 19 20 30 36 43 45 48 50 55 (Sorted)

The important thing with shellsort is deciding on the increment sequence of each sub-collection. From what I can tell, there isn’t any definitive method and depending on the order of your elements, different increment sequences may perform better than others.

There are however certain increment sequences that you may want to avoid. An even based increment sequence (e.g. 2 4 8 16 32 …) should typically be avoided because it does not allow for even elements to be compared with odd elements until the final sort phase – which in a way would negate many of the benefits of using sub-collections.

The performance on the number of comparisons and item movements of Shellsort is hard to determine, however it is considered to be considerably better than the normal insertion sort.

Quicksort
Quicksort uses a divide and conquer approach to sort a collection of items. The collection is divided into two sub-collections – and the two sub-collections are sorted and combined into one list in such a way that the combined list is sorted.

The algorithm is in general pseudo code below…

Divide the collection into two sub-collections
Quicksort the lower sub-collection
Quicksort the upper sub-collection
Combine the lower & upper sub-collection together
As hinted at above, quicksort uses recursion in its implementation.

The real trick with quicksort is to get the lower and upper sub-collections to be of equal size. The size of a sub-collection is determined by what value the pivot is. Once a pivot is determined, one would partition to sub-collections and then repeat the process on each sub collection until you reach the base case.

With quicksort, the work is done when dividing the sub-collections into lower & upper collections. The actual combining of the lower & upper sub-collections at the end is relatively simple since every element in the lower sub-collection is smaller than the smallest element in the upper sub-collection.

Mergesort
With quicksort, the average-case complexity was O(nlog2n) however the worst case complexity was still O(N*N). Mergesort improves on quicksort by always having a complexity of O(nlog2n) regardless of the best or worst case. So how does it do this?

Mergesort makes use of the divide and conquer approach to partition a collection into two sub-collections. It then sorts each sub-collection and combines the sorted sub-collections into one sorted collection.

The general algorithm for mergesort is as follows…

Divide the collection into two sub-collections
Mergesort the first sub-collection
Mergesort the second sub-collection
Merge the first sub-collection and the second sub-collection
As you can see.. it still pretty much looks like quicksort – so lets see where it differs…

Firstly, mergesort differs from quicksort in how it partitions the sub-collections. Instead of having a pivot – merge sort partitions each sub-collection based on size so that the first and second sub-collection of relatively the same size. This dividing keeps getting repeated until the sub-collections are the size of a single element.

If a sub-collection is one element in size – it is now sorted! So the trick is how do we put all these sub-collections together so that they maintain their sorted order.

Sorted sub-collections are merged into a sorted collection by comparing the elements of the sub-collection and then adjusting the sorted collection. Lets have a look at a few examples…

Assume 2 sub-collections with 1 element each

10 & 20

Compare the first element of the first sub-collection with the first element of the second sub-collection. Take the smallest of the two and place it as the first element in the sorted collection. In this scenario 10 is smaller than 20 so 10 is taken from sub-collection 1 leaving that sub-collection empty, which means by default the next smallest element is in sub-collection 2 (20).

So the sorted collection would be 10 20

Lets assume 2 sub-collections with 2 elements each

10 20 & 15 19

So… again we would

Compare 10 with 15 – 10 is the winner so we add it to our sorted collection (10) leaving us with 20 & 15 19
Compare 20 with 15 – 15 is the winner so we add it to our sorted collection (10 15) leaving us with 20 & 19
Compare 20 with 19 – 19 is the winner so we add it to our sorted collection (10 15 19) leaving us with 20 & _
20 is by default the winner so our sorted collection is 10 15 19 20.
Make sense?

Heapsort (still needs to be completed)
So by now I am tired of sorting algorithms and trying to remember why they were so important. I think every year I go through this stuff I wonder to myself why are we made to learn about selection sort and insertion sort if they are so bad – why didn’t we just skip to Mergesort & Quicksort. I guess the only explanation I have for this is that sometimes you learn things so that you can implement them in future – and other times you learn things so that you know it isn’t the best way of implementing things and that you don’t need to implement it in future. Anyhow… luckily this is going to be the last one of my sorts for today.

The first step in heapsort is to convert a collection of data into a heap. After the data is converted into a heap, sorting begins…

So what is the definition of a heap? If we have to convert a collection of data into a heap, how do we know when it is a heap and when it is not?

The definition of a heap is as follows: A heap is a list in which each element contains a key, such that the key in the element at position k in the list is at least as large as the key in the element at position 2k +1 (if it exists) and 2k + 2 (if it exists).

Does that make sense? At first glance I’m thinking what the heck??? But then after re-reading my notes I see that we are doing something different – up to now we have really looked at data as an array or sequential collection of data that we need to sort – a heap represents data in a slightly different way – although the data is stored in a sequential collection, for a sequential collection of data to be in a valid heap – it is “semi sorted”.

Let me try and explain a bit further with an example…

Example 1 of Potential Heap Data

Assume we had a collection of numbers as follows 1[1] 2[2] 3[3] 4[4] 5[5] 6[6]

For this to be a valid heap

element with value of 1 at position [1] needs to be greater or equal to the element at position [3] (2k +1) and position [4] (2k +2). So in the above example, the collection of numbers is not in a valid heap.

Example 2 of Potential Heap Data

Lets look at another collection of numbers as follows 6[1] 5[2] 4[3] 3[4] 2[5] 1[6]

Is this a valid heap?

Well… element with the value 6 at position 1 must be greater or equal to the element at position [3] and position [4]. Is 6 > 4 and 6 > 3?

Yes it is.

Lets look at element 5 as position 2. It must be greater than the values at [4] & [5]. Is 5 > 3 and 5 > 2?

Yes it is.

If you continued to examine this second collection of data you would find that it is in a valid heap based on the definition of a heap.
