---
layout: post
title: In-place Algorithm
date: 2024-05-15 10:33:00 +0900
categories: algorithm
---
## Definition
In-place algorithm is an algorithm that transforms input using a small, constant amount of extra storage space.  
Usually, the extra storage space is used during the swap stage to keep track of the current variable.

## Characteristics
- Constant Space Complexity
> In-place algorithm typically uses O(1) space.
- Data Modification
> Input data is directly modified without requiring any additional memory.
- Efficiency 
> In-place algorithms are memory efficient, making them suitable for large data sets or  
codes with limited memory storage.



## Benefits
- Memory Efficient
> Uses minimum memory.

- Avoids <span class="hover-container"><span class="hover-target">Memory Overhead</span>Memory overhead<span class="info-box">Memory overhead refers to extra memory space consumed by a program/process beyond the actual data needed.</span></span>
>  By limiting the extra space used, these algorithms avoid the overhead  
associated with dynamic memory allocation and deallocation
- Speed Improvement
> Reduced memory allocation, which leads to faster performance.

## Drawbacks
- Complex
> Often more complex to implement than out-of-place algorithms such as Merge Sort.
- Debug Difficulty
> Modifies the original input data, which leads to more difficult debugging or error recovery.


## Examples of In-Place Algorithms
### Sorting Algorithms
- Bubble Sort
> Swaps elements in the same array.
- Insertion Sort
> Shifts elements within the array.
- Selection Sort
> Swaps elements within the array.
- Quick Sort
> Recursively sorts the elements.

### Array Manipulation
- Reversing an Array
> Swaps elements from both ends moving towards the center.
- In-place Rotation
> Rotates elements within the array.


<style>
.hover-container {
    position: relative;
    display: inline-block;
}

.hover-target {
    text-decoration: underline;
    cursor: pointer;
}

.info-box {
    visibility: hidden;
    width: 200px;
    background-color: #555;
    color: #fff;
    text-align: center;
    border-radius: 5px;
    padding: 10px;
    position: absolute;
    z-index: 1;
    bottom: 125%; /* Position above the hover element */
    left: 50%;
    margin-left: -100px; /* Center the box */
    opacity: 0;
    transition: opacity 0.3s;
}

.hover-container:hover .info-box {
    visibility: visible;
    opacity: 1;
}
</style>