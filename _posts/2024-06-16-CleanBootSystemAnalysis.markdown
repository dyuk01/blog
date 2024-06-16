---
layout: post
title: Clean Boot & System Analysis
date: 2024-06-15
categories: tutorial
---

## Problem
I noticed that my desktop was having problem with its storage partition, since my disk was storing about double the intended file size. Because I did not know the exact reason for this problem, I decided to clean boot and run system analysis to fix the issue.

## Clean Boot
1. Type 'msconfig' into the search bar, and click 'Service'.
2. After clicking 'Hide Microsoft Service', check 'Disable All' and Confirm.
3. Reboot

## System Analysis
1. Press 'Windows Key' + 'X' which should enable a list of tabs on the bottom
2. Click 'command prompt(admin)'
3. Now, enter the following command:
```console
Dism /online /cleanup-image /restorehealth
```
4. After the scan, enter the following command :
```console
sfc /scannow
```
5. Restart the computer

---