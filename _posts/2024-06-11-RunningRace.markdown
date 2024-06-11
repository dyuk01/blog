---
layout: post
title: Running Race
date: 2024-06-11
categories: programmers python
---

## Problem
![alt text](/blog/public/img/RunningRace.png)

## Translation
Every year, a running race is held in Yan. The commentators call out the name of the player who overtakes the player immediately in front of them. For example, if the players are running in the order of "mumu", "soe", and "poe" from 1st to 3rd place, and the commentator calls out the name "soe", it means that the 2nd place player "soe" has overtaken the 1st place player "mumu". As a result, "soe" becomes 1st, and "mumu" becomes 2nd.

Given a string array players containing the names of the players in the order from 1st place to the current rank, and a string array callings containing the names called out by the commentators, complete the function solution that returns the names of the players in the order from 1st place to the current rank after the race is over.

## Approach


## Code
```python
def solution(players, callings):
    # Creates a dictionary for the players with their current position
    player_pos = {player: idx for idx, player in enumerate(players)}
    for calling in callings:
        current_pos = player_pos[calling]
        if current_pos > 0:
            player_infront = players[current_pos - 1]
            # Swap names
            players[current_pos], players[current_pos - 1] = players[current_pos - 1], players[current_pos] 
            # Swap position
            player_pos[calling] -= 1
            player_pos[player_infront] += 1
    return players
```

## Time Complexity
O(n)
> The functions (.lower(), .sub(), .strip()) used throughout the algorithm iterates through the length of the array. Thus, O(n)

## Space Complexity
O(n)
> Space of O(n) is required when the functions alter the characters of the input string

---