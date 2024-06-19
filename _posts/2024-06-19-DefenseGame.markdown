---
layout: post
title: Defense Game
date: 2024-06-19
categories: programmers python
---

## Problem
![alt text](/blog/public/img/DefenseGame.png)

## Translation
Junho is currently obsessed with a defense game. The defense game involves Junho using n soldiers to sequentially block the attacks of enemies. The game proceeds according to the following rules:

- Junho starts with 'n' soldiers.
- Each round, 'enemy[i]' number of enemies appear.
- Junho can use up to 'enemy[i]' soldiers to block 'enemy[i]' enemies.
    - For example, if there are 7 soldiers left and 2 enemies appear, blocking this round will leave 7 - 2 = 5 soldiers.
    - If the number of remaining soldiers is less than the number of enemies in the current round, the game ends.
- There is a skill called "invincibility", which allows blocking an attack for one round without using any soldiers.
    - The "invincibility" skill can be used up to 'k' times.
Junho wants to use the "invincibility" skill at the right time to progress through the maximum number of rounds.<br>
Please complete the solution function to return how many rounds Junho can block, given the initial number of soldiers 'n', the number of times the "invincibility" skill can be used 'k', and the array 'enemy' that contains the number of enemies attacking in each round.

## Approach
There are multiple ways to approach the problem<br>

1. Calculate every possible ways that the user can use their "invincibility" skill, and find the maximum round that one can go.
> Uses nested for loop to calculate every possible scenario.

```python
def solution(n, k, enemy):
    for i in range(len(enemy) - 2):
        for j in range(i + 1, len(enemy) - 1):
            for k in range(j + 1, len(enemy)):
                # Rounds that the user used "Invincibility" skill will turn the number of enemies to 0
                dp = enemy
                dp[i] = dp[j] = dp[k] = 0
                rounds = res = 0
                life = n
                for e in dp:
                    life -= e
                    if life < 0:
                        break
                    rounds += 1
                if rounds > res:
                    res = rounds
    return res
```

2. Proceed the game regardless of the number of allies. If current allies become negative integer, consider using "invincibility" as "revive" skill, where you add the maximum number of enemies that you defeated to the number of allies.
> Uses list or heap to store and pop the number of defeated enemies

```python
import heapq

def solution(n, k, enemy):
    def_enemies = []
    for i in range(len(enemy)):
        # Because heap's default is stored as min-heap, storing and returning the integer as negative will find the max
        heapq.heappush(def_enemies, -enemy[i]) # heapq.heappush(def_enemies, (-enemy[i], enemy[i]))
        n -= enemy[i]
        if n < 0:
            if k > 0:
                n += heapq.heappop(def_enemies) # n += heapq.heappop(def_enemies)[1]
                k -= 1
            else :
                return i
    return len(enemy)
```

## Code
Because I want the code to have lowest time complexity as possible, I will be choosing step 2 (using heap).

```python
import heapq

def solution(n, k, enemy):
    def_enemies = []
    for i in range(len(enemy)):
        # Because heap's default is stored as min-heap, storing and returning the integer as negative will find the max
        heapq.heappush(def_enemies, -enemy[i]) # heapq.heappush(def_enemies, (-enemy[i], enemy[i]))
        n -= enemy[i]
        if n < 0:
            if k > 0:
                n += heapq.heappop(def_enemies) # n += heapq.heappop(def_enemies)[1]
                k -= 1
            else :
                return i
    return len(enemy)
```

## Time Complexity
O(n)
> 
## Space Complexity
O(n)
> 

---