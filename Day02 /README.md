# Add Two Numbers Solution

## Problem Statement
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in **reverse order**, and each of their nodes contains a **single digit**. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

## Implementation
This Python solution iterates through the linked lists `l1` and `l2`, performing digit-wise addition while managing carry-over values. A dummy head node is used to simplify handling the linked list structure.

## Code
```python
from typing import Optional

class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

class Solution:
    def addTwoNumbers(
        self, l1: Optional[ListNode], l2: Optional[ListNode]
    ) -> Optional[ListNode]:
        dummyHead = ListNode(0)
        curr = dummyHead
        carry = 0
        while l1 != None or l2 != None or carry != 0:
            l1Val = l1.val if l1 else 0
            l2Val = l2.val if l2 else 0
            columnSum = l1Val + l2Val + carry
            carry = columnSum // 10
            newNode = ListNode(columnSum % 10)
            curr.next = newNode
            curr = newNode
            l1 = l1.next if l1 else None
            l2 = l2.next if l2 else None
        return dummyHead.next
```

## Explanation
1. Initialize a `dummyHead` node to help manage the resulting linked list.
2. Use a `carry` variable to handle sums greater than 9.
3. Traverse `l1` and `l2`, adding corresponding node values and updating `carry`.
4. Create new nodes in the result list to store the sum of each digit pair.
5. If a carry remains after traversal, add an extra node.
6. Return `dummyHead.next`, which points to the resulting linked list.

## Example Usage
```python
def linked_list_from_list(lst):
    dummy = ListNode(0)
    curr = dummy
    for num in lst:
        curr.next = ListNode(num)
        curr = curr.next
    return dummy.next

def print_linked_list(node):
    result = []
    while node:
        result.append(str(node.val))
        node = node.next
    print(" -> ".join(result))

l1 = linked_list_from_list([2, 4, 3])  # Represents number 342
l2 = linked_list_from_list([5, 6, 4])  # Represents number 465
solution = Solution()
result = solution.addTwoNumbers(l1, l2)  # Expected output: 7 -> 0 -> 8
print_linked_list(result)
```

## Time Complexity
- **O(max(m, n))**: The solution processes each node once, where `m` and `n` are the lengths of `l1` and `l2`.

## Space Complexity
- **O(max(m, n))**: The solution stores the sum in a new linked list, requiring space proportional to the longest input list.
