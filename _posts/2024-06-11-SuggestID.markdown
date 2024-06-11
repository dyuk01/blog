---
layout: post
title: Suggest ID
date: 2024-06-11
categories: programmers python
---

## Problem
![alt text](/blog/public/img/SuggestID.png)
Translation :  
Neo, a new developer who joined Kakao, has been assigned to the "Kakao Account Development Team" and is tasked with creating IDs for users who join the Kakao service. Neo's first task is to develop a program that recommends IDs to new users who enter IDs that do not comply with Kakao ID rules. The following are the rules for Kakao IDs.  
  
The length of the ID must be between 3 and 15 characters.  
IDs can only contain lowercase letters, numbers, hyphens (-), underscores (_), and periods (.).  
However, periods (.) cannot be used at the beginning or end and cannot be used consecutively.  
Neo is to develop a program that recommends new IDs that comply with the Kakao ID rules in the following seven-step sequential process when a new user enters an ID that does not comply with the rules.

## Approach
The goal is to follow the restrictions and suggest the correct formatted ID.  
1. Limit ID Length
2. Remove special characters with exceptions
3. Remove repeating '.'
4. Remove initial and trailing '.'

## Code
```python
import re

def solution(new_id):
    special_ch = r'[^a-zA-Z0-9\-_.]'
    
    # lowercase
    new_id = new_id.lower()
    # only include isalnum, [-, _, .]
    new_id = re.sub(special_ch, '', new_id)
    # replace any repeating '.' to one '.'
    new_id = re.sub(r'\.{2,}', '.', new_id)
    # exclude first and last '.'
    new_id = new_id.strip('.')
    if new_id == '':
        new_id = 'a'

    if len(new_id) > 15:
        new_id = new_id[:15]
        new_id = new_id.rstrip('.')

    while len(new_id) < 3:
        new_id += new_id[-1]

    return new_id
```

## Time Complexity
O(n)
> The functions (.lower(), .sub(), .strip()) used throughout the algorithm iterates through the length of the array. Thus, O(n)

## Space Complexity
O(n)
> Space of O(n) is required when the functions alter the characters of the input string

---