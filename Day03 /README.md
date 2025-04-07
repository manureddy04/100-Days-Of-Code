Longest Substring Without Repeating Characters

## Problem Statement
Given a string `s`, find the **length of the longest substring** without repeating characters.

### Constraints:
- `0 <= s.length <= 5 * 10^4`
- `s` consists of English letters, digits, symbols, and spaces.

### Example 1:
Input: s = "abcabcbb" Output: 3 Explanation: The longest substring without repeating characters is "abc", which has a length of 3.

shell
Copy
Edit

### Example 2:
Input: s = "bbbbb" Output: 1 Explanation: The longest substring without repeating characters is "b", which has a length of 1.

shell
Copy
Edit

### Example 3:
Input: s = "pwwkew" Output: 3 Explanation: The longest substring without repeating characters is "wke", which has a length of 3.

sql
Copy
Edit

---

## Implementation
This Python solution uses a **sliding window approach** with a **set** to efficiently track unique characters in the substring.

## Code
```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        n = len(s)
        maxLength = 0
        charSet = set()
        left = 0
        
        for right in range(n):
            if s[right] not in charSet:
                charSet.add(s[right])
                maxLength = max(maxLength, right - left + 1)
            else:
                while s[right] in charSet:
                    charSet.remove(s[left])
                    left += 1
                charSet.add(s[right])
        
        return maxLength
Explanation
Uses a set (charSet) to store unique characters in the current substring.

Maintains two pointers:

left: Start of the substring

right: End of the substring (iterating through s)

Expands right while adding unique characters.

If a duplicate is found, moves left forward while removing characters until no duplicates remain.

Updates maxLength with the maximum window size encountered.

Returns maxLength at the end.

Complexity Analysis
Time Complexity: O(n) → Each character is added and removed from the set at most once.

Space Complexity: O(min(n, 26)) → The set stores at most 26 unique characters (for lowercase English letters).


