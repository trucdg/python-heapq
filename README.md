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
| 4 | heappushpop | push and pop element into and out of the heap. The function first pushes the provided element to the heap and then pops the smallest element from the heap. | O(log(n)) |
| 5 | heapreplace | push and pop elements in the heap. But instead of push then pop, it first pops the smallest element from the heap, then pushes the provided element back into the heap (the order is in reverse with **heappushpop** | O(log(n)) |
| 6 | nlargest | returns the k-largest elements from the heap | O(log(k)) |
| 7 | nsmallest | returns the k-smallest elements from the heap | O(log(k)) |

# Heap in Python
```python
# Import heapq module to implement heap
import heapq

# Initialize arr
arr = [9, 7, 2, 8, 6]

# use heapify to convert array into a heap
heapq.heapify(arr)
# push element into the heap
heapq.heappush(arr,1)
# pop element from the heap
heapq.heappop(arr)
# simultaneously push and then pop
heapq.heappushpop(arr,10)

```

## Heap Data Structure Operations
We will be discussing these operations over a max-heap since the same operations can be applied to a min-heap
**Insertion in heap:**
Consider we have an array with elements **10,8,5,15,6** in it. To build a max-heap using the given elements, we perform the following steps:
1. **Add the first element**, **10** is in the tree. It is the root of the tree.
2. **Add the next element in the tree. Compare it with the parent element.** If it is greater than its parent element, swap their positions. It is done to ensure that thee tree follows **heap** conditions. Here, 8 is inserted as the left child of the root element because **heap is filled from left to right**. No swapping occurs because 10 > 8.
   
<img src="https://github.com/trucdg/python-heapq/assets/91285203/40af7f45-cbb3-42c7-a0e6-aa9d5ab39adc" width="500" height="400">

4. **Repeat the above step with the next element**
   
<img src="https://github.com/trucdg/python-heapq/assets/91285203/7b00c837-d6d6-4748-bf00-18d7a348c5c9" width="500" height="400">

6. **Add the next element**, 15 in the tree.
   
<img src="https://github.com/trucdg/python-heapq/assets/91285203/50f0f8bd-29f8-42ba-9013-1b5ca0ca4dc7" width="500" height="400">

Now, since **15** is greater than its parent element **8**,  this tree is not a **max-heap** anymore. To make it a **heap** again, we will swap the position of **8** and **15**.

![image](https://github.com/trucdg/python-heapq/assets/91285203/7507fa02-5354-44a7-b220-e4025ab8fc31)


Again, the obtained tree is not a max-heap since 15 > 10 (its parent). We will swap the position of **10** and **15**.

![image](https://github.com/trucdg/python-heapq/assets/91285203/e43bace2-bb67-4db7-8f90-d72907c1e09e)

This step is performed using recursion, and done until the inserted element finds its correct position in the heap.

*Notice that **15** was first added at the bottom of the tree and then moved up to its correct position. This moving up of elements known as **bubbling up***

**5. Add the last element**, 6 in the heap

![image](https://github.com/trucdg/python-heapq/assets/91285203/9b2a799f-05fe-47f1-88ec-3561a063697f)

One thing to note here is that a comparison is done each time an element is added. The number of comparisons also depends on the height of the tree. In the above case, a total of 5 comparisons were made. This results in a time complexity of O(nlog(n)) since the **height of a binary tree** is **log(n)** (There are n nodes. Each node, in the worst case, needs to be bubbled up log(n) levels -> nlog(n))

But we cam reduce the number of comparisons by using a method called **heapify** where elements are first added into the tree and then arranged in a bottom-up fashion. It helps in reducing the number of comparisons, and thus the time complexity of the overall algorithm is O(n) (linear - using heapify).


## How to HEAPIFY a Binary Tree?
**Heapify** is the process of rearranging the elements to form a tree that maintains the properties of the **heap data structure.**

Recall the **list/array** that had the elements - [10, 8, 5, 15, 6] in it. To **heapify** these elements, and form a **max-heap**, we follow the following steps:
- **1. Visualize all the elements of the list as a complete binary tree**
  
Treat the elements of the given array as the nodes of a tree. Notice how tha below binary tree is a *complete binary tree* but DOESN'T satisfy the properties of a **max-heap** since element 8 has an element greater than itself as its *child*.

![image](https://github.com/trucdg/python-heapq/assets/91285203/2b4cf965-2685-4546-b65c-35da66de2977)


- **2. Construct the heap property using swapping and comparison**

Start from comparing the values of children nodes with that of the parent. If the parent is smaller than the values of the children, swap it. Swapping is done with the **larger of the 2 children**. This process is repeated until every node satisfy the property of a *max-heap*.

Here, we start comparing 8 with 15 and 6. Since 15 > 6 (15 is the larger of the 2 children of 8), and 15 > 8, we swap their positions. 

![image](https://github.com/trucdg/python-heapq/assets/91285203/514c44cd-ef53-450a-a1a5-9663a14c23b0)

Again, the max-heap property is still not satisfied since 15 > 10. Therefore, we perform the above step again

![image](https://github.com/trucdg/python-heapq/assets/91285203/8c284991-4ac1-4609-9b65-e15dbe545ded)

**Note:**
- One interesting thing to note here is that **a note can be heapified if and only if all the children nodes are already heapified. This is the reason why we *start from the bottom-most-sub-tree***.
- This step is also performed using recursion. We create a function called heapify() that works by dividing the tree into smaller sub-trees and then comparing the values of parents with that of children in each sub-tree.
- Notice that the number of comparisons are reduced slightly. This way, we can significantly reduce the comparisons if there are many elements to be added.
- Here, the time complexity would be equal to the height of tree O(logn). This is because a node will be compared only to its parents, and thus, will be swapped at most O(logn) times.

## DELETION from HEAP

Let us consider the following max-heap

![image](https://github.com/trucdg/python-heapq/assets/91285203/89d124a7-e5e4-4533-b882-723cf55201e9)

To delete the elements from a heap, we follow the below steps:
- **1. Search for the element to be deleted and swap it with the last element in the heap**. Let's say we want to delete 10
We first want to swap 10 with 6 (which is the last element):

![image](https://github.com/trucdg/python-heapq/assets/91285203/90b93f83-48bc-42c3-b939-2e58e6866923)

- **2. Remove the element from the tree.**

Notice that the remaining heap has lost the max-heap property. So in the next step, we need to heapify it again.

![image](https://github.com/trucdg/python-heapq/assets/91285203/689cbbcb-1495-4a7a-b018-965829aafaf8)

- **3. Heapify the tree again.**
- 
![image](https://github.com/trucdg/python-heapq/assets/91285203/2947efd5-ab3b-4126-984c-9f38834aaef0)





































