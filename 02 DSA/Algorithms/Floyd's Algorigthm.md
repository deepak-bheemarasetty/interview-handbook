## Overview
1. This is an Algorithm for cycle detection.
2. It is frequently used in problems where finding a duplicate element is necessary within a constaints.

## Core Idea
1. Use two pointers a fast pointer and a slow pointer. Start both at first index.
2. Slow pointer moves one step at a time while the fast pointer moves by 2 steps. (A step is referred as Jumping to index of current index's value).
3. After both slow and fast pointers meet. Reset slow pointer to first index.
4. Now move both slow and fast pointers at same pace and find where they're meeting. The value of the index where both slow and fast pointer meet for the second time is Duplicate Element.

## Complexity

- Time: `O(n)`
- Space: `O(1)`