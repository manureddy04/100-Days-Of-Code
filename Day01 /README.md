# Two Sum Solution

## Problem Statement
Given an array of integers `nums` and an integer `target`, return indices of the two numbers that add up to `target`.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

## Implementation
This Python solution iterates through the `nums` list using a nested loop to find a pair of numbers that add up to the given `target`. If such a pair is found, their indices are returned.

## Code
```python
from typing import List

class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in range(len(nums)):
            for j in range(i + 1, len(nums)):
                if nums[j] == target - nums[i]:
                    return [i, j]
        # Return an empty list if no solution is found
        return []
```

## Explanation
1. Iterate over the array with an index `i`.
2. For each `i`, iterate over the subsequent elements with index `j`.
3. Check if `nums[j]` is equal to `target - nums[i]`.
4. If a match is found, return the indices `[i, j]`.
5. If no match is found, return an empty list.

## Example Usage
```python
solution = Solution()
nums = [2, 7, 11, 15]
target = 9
print(solution.twoSum(nums, target))  # Output: [0, 1]
```

## Time Complexity
- **O(n²)**: The solution uses a nested loop, making it less efficient for large inputs.

## Space Complexity
- **O(1)**: No additional data structures are used, only variables.

