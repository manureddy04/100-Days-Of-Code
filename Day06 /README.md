# Zigzag Conversion

## Problem Statement
The string `"PAYPALISHIRING"` is written in a zigzag pattern on a given number of rows like this (you may want to display this pattern in a fixed font for better legibility):

P A H N A P L S I I G Y I R

yaml
Copy
Edit

And then read line by line: `"PAHNAPLSIIGYIR"`

Write the code that will take a string and convert it to this zigzag pattern given a number of rows.

### Constraints:
- `1 <= s.length <= 1000`
- `s` consists only of **English letters** (uppercase and lowercase).
- `1 <= numRows <= 1000`

---

## Example 1:
Input: s = "PAYPALISHIRING", numRows = 3 Output: "PAHNAPLSIIGYIR"

shell
Copy
Edit

## Example 2:
Input: s = "PAYPALISHIRING", numRows = 4 Output: "PINALSIGYAHRPI" Explanation: P I N A L S I G Y A H R P I

sql
Copy
Edit

---

## Implementation
This solution simulates the zigzag pattern by maintaining **multiple row lists** and appending characters accordingly.

## Code
```python
class Solution:
    def convert(self, s: str, numRows: int) -> str:
        if numRows == 1 or numRows >= len(s):
            return s

        idx, d = 0, 1
        rows = [[] for _ in range(numRows)]

        for char in s:
            rows[idx].append(char)
            if idx == 0:
                d = 1
            elif idx == numRows - 1:
                d = -1
            idx += d

        for i in range(numRows):
            rows[i] = ''.join(rows[i])

        return ''.join(rows)
Explanation
Base Case: If numRows == 1, return s as no zigzag is needed.

Simulating Zigzag Movement:

Maintain numRows lists to store characters for each row.

Use idx to track the current row and d to track direction (down or up).

Move down (idx += 1) until the last row, then switch direction (d = -1).

Move up (idx -= 1) until the first row, then switch direction (d = 1).

Joining Rows: After processing all characters, concatenate all rows to get the final string.

Complexity Analysis
Time Complexity: O(n) → Each character is processed once.

Space Complexity: O(n) → Extra space is used for row storage.
