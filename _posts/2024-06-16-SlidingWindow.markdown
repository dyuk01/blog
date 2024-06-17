---
layout: post
title: Sliding Window
date: 2024-06-16
categories: algorithm 
---

## When to use
1. Problem input is linear data structure (array, string, linked list)
2. Asked to find longest/shortest substring, subarray, or a value

## How it works
Sliding window is used to perform a required operation on a specific window size of a given array or linked list.  
> 1. Start from 1st element and keep shifting by 1 element to the right
  2. Ajust the length of the window according to the problem 
![alt text](/blog/public/img/SlidingWindow.png)

## Types
1. Fast/Slow
> Have a fast pointer that grows window under certain condition, then have a slow pointer that shrinks the window after the condition is met

2. Fast/Catchup
> Similar to fast/slow method, but slow pointer doesn't gradually shrinks the window. Slow pointer immediately jumps to the fast pointer's position when the condition is met.

3. Fast/Lagging
>

4. Front/Back
>

---