# Median of Two Sorted Arrays

## Problem Statement
Given two sorted arrays `nums1` and `nums2`, return the **median** of the two sorted arrays.

The overall run time complexity should be **O(log (m+n))**.

### Constraints:
- `0 <= nums1.length, nums2.length <= 1000`
- `-10^6 <= nums1[i], nums2[i] <= 10^6`
- The input arrays are sorted in **non-decreasing order**.

### Example 1:
Input: nums1 = [1, 3], nums2 = [2] Output: 2.0 Explanation: Merging the arrays results in [1, 2, 3]. The median is 2.0.

shell
Copy
Edit

### Example 2:
Input: nums1 = [1, 2], nums2 = [3, 4] Output: 2.5 Explanation: Merging the arrays results in [1, 2, 3, 4]. The median is (2 + 3) / 2 = 2.5.

yaml
Copy
Edit

---

## Implementation
This solution merges both arrays and sorts them, then finds the median based on the total count.

## Code
```python
class Solution:
    def findMedianSortedArrays(self, nums1, nums2):
        # Merge the arrays into a single sorted array.
        merged = nums1 + nums2

        # Sort the merged array.
        merged.sort()

        # Calculate the total number of elements in the merged array.
        total = len(merged)

        if total % 2 == 1:
            # If the total number of elements is odd, return the middle element as the median.
            return float(merged[total // 2])
        else:
            # If the total number of elements is even, calculate the average of the two middle elements as the median.
            middle1 = merged[total // 2 - 1]
            middle2 = merged[total // 2]
            return (float(middle1) + float(middle2)) / 2.0
Explanation
Merge the two arrays into a single list.

Sort the merged list to ensure elements remain in order.

Find the median:

If the total number of elements is odd, return the middle element.

If the total number of elements is even, return the average of the two middle elements.

Complexity Analysis
Time Complexity: O((m+n) log(m+n)) → Due to sorting.

Space Complexity: O(m+n) → Due to merging the arrays.

Note: This is not the optimal approach. A more efficient method using binary search can achieve O(log (m+n)) complexity.


