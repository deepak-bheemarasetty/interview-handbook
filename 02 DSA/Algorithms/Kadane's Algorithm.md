
## Problem

Maximum subarray sum using Kadane's algorithm.

## Core Idea

Track the best subarray sum ending at the current index, then keep the best overall sum seen so far.

## Key Insight

If the running sum becomes worse than starting fresh at the current element, reset it.

## Algorithm

1. Initialize `current_sum` and `best_sum` with the first element.
2. For each next element:
   - `current_sum = max(element, current_sum + element)`
   - `best_sum = max(best_sum, current_sum)`
3. Return `best_sum`.

## Complexity

- Time: `O(n)`
- Space: `O(1)`

## What I Learned

- Kadane's algorithm is a greedy dynamic choice at each step.
- The running sum should not be forced to carry forward a negative prefix.
- The "maximum subarray" answer is built from local best ending here, not only a global prefix sum.

## Common Mistake

- Assuming the best subarray must include earlier elements even when the running sum has already gone negative.
