# 🎯 Heap in Python
## Overview
A heap is simply a binary tree with some additional rules that it has to follow. There are 2 rules which differentiate heap structures from any other tree structure.

These rules are:
1. A heap must be a **complete binary tree**
2. It must statisfy the **heap property**. It means that all the children of a given node must be greater than the parent node (min heap), or all of the children node must be smaller than the parent node (max heap)

![image](https://github.com/trucdg/python-heapq/assets/91285203/7e6dbbb7-c7b9-4323-9a62-816069eeb3f6)

>**Takeaways**
>
> Complexity of Heap Data Structure
> 
>| Operation | Time Complexity |
>| --- | --- |
>| Get Max or Min element | O(1) - element is at the root node |
>| Remove Max or Min element | O(log(n)) - sift down or sift up to maintain heap property after removal |
>| Insert an Element| O(logn(n)) - always insert at the end of the array, then sift up |

## Heap Data Structure
### Array Representation
Heap Data Structure is a complete binary tree data structure. One of the most interesting properties of a **binary tree** is that we can use array representation. And, the indexes of the elements in the array can be used to find the parent or children of any node.
*Note: Array can only be used as representation for complete binary trees*

To further explain this, consider the following tree. It has 7 nodes, and each node can be arranged as an element of an array.
![image](https://github.com/trucdg/python-heapq/assets/91285203/e689a237-bcee-4b6b-a875-73b769c0b275)
![image](https://github.com/trucdg/python-heapq/assets/91285203/2d740a5f-32c2-449b-a478-bbdca2530d83)

Now, the index of a given element is **i**,
- Its LEFT child: **2i+1**
- Its RIGHT child: **2i+2**
- Its PARENT: **(i-1)/2** (int division)

### Types of Heap Data Structure


## Heap Python Module
In python, you have the **heapq** module, with which you can create a min heap or max heap. When you create a heap using **heapq** function, **by default, the heap will always be the minheap**, meaning that each time the smallest element is popped from the heap.

The **heapq** module has some relevant functions to perform various operations on the heap data structure.
These functions are given below:


| Num | Operation | Description | TC |
| ------------- | ------------- | ------------- | ------------- | 
| 1 | heapify | converts an iteratble into a heap data structure, in-place, in linear time. After using this function, the heap's elements will be reordered so that it has the property of a min heap| O(n) |
| 2 | heappush| inserts an element into a heap, and after insertion, the order is adjusted accordingly so that the heap structure is maintained. | O(log(n)) |
| 3 | heappop | removes and returns the smallest element of the heap, and after removal, the order is adjusted accordingly so that the heap structure is maintained. | O(log(n))|
| 4 | heappushpop | push and pop lement into and out of the heap. The function first pushes the provided element to the heap and then pops the smallest element from the heap. | O(log(n)) |
| 5 | heapreplace | push and pop elements in the heap. But instead of push then pop, it first pops the smallest element from the heap, then pushes the provided element back into the heap (the order is in reverse with **heappushpop** | O(log(n)) |
| 6 | nlargest | returns the k-largest elements from the heap | O(log(k)) |
| 7 | nsmallest | returns the k-smallest elements from the heap | O(log(k)) |













































