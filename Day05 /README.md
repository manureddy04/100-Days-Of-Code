# Longest Palindromic Substring

## Problem Statement
Given a string `s`, return the **longest palindromic substring** in `s`.

A **palindrome** is a string that reads the same forward and backward.

### Constraints:
- `1 <= s.length <= 1000`
- `s` consists only of **ASCII** printable characters.

---

## Example 1:
Input: s = "babad" Output: "bab" Explanation: "aba" is also a valid answer.

shell
Copy
Edit

## Example 2:
Input: s = "cbbd" Output: "bb"

python
Copy
Edit

---

## Implementation
This solution uses the **expand around center** technique to efficiently find the longest palindromic substring.

## Code
```python
class Solution:
    def longestPalindrome(self, s: str) -> str:
        if len(s) <= 1:
            return s

        def expand_from_center(left, right):
            while left >= 0 and right < len(s) and s[left] == s[right]:
                left -= 1
                right += 1
            return s[left + 1:right]

        max_str = s[0]

        for i in range(len(s) - 1):
            odd = expand_from_center(i, i)
            even = expand_from_center(i, i + 1)

            if len(odd) > len(max_str):
                max_str = odd
            if len(even) > len(max_str):
                max_str = even

        return max_str
Explanation
Expand Around Center Approach:

A palindrome expands symmetrically from its center.

We check both odd-length (single-character center) and even-length (two-character center) palindromes.

Steps:

Define a helper function expand_from_center(left, right).

Iterate over each index i:

Expand around i (odd-length palindromes).

Expand around i and i+1 (even-length palindromes).

Update the max_str with the longest palindrome found.

Complexity Analysis
Time Complexity: O(n²) → Expanding from each center takes O(n), and there are O(n) centers.

Space Complexity: O(1) → No extra space is used apart from variables.

Note: There is an optimized approach using Manacher's Algorithm which runs in O(n) time, but this method is simpler and still efficient for most cases.
