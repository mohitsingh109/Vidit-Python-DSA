# Linked List Learning Guide

## 1. Introduction to Linked List
A **linked list** is a linear data structure where elements (called nodes) are connected using pointers.  
Each node contains:
- **Data** – value stored in the node
- **Next** – reference to the next node in the list  

### Types of Linked Lists:
1. **Singly Linked List** – each node points to the next.
2. **Doubly Linked List** – nodes have pointers to both previous and next nodes.
3. **Circular Linked List** – last node points back to the head.

**Why Linked List?**
- Dynamic size (no need to predefine capacity like arrays).
- Efficient insertions and deletions (O(1) if reference to node is known).

---

## 2. Common Operations on Linked List

| Operation | Singly LL | Doubly LL | Time Complexity | Space Complexity |
|-----------|-----------|-----------|-----------------|------------------|
| Insert at Head | O(1) | O(1) | O(1) | O(1) |
| Insert at Tail | O(n) | O(1) | O(n) / O(1) | O(1) |
| Delete Node | O(n) | O(n) | O(n) | O(1) |
| Search Element | O(n) | O(n) | O(n) | O(1) |
| Reverse List | O(n) | O(n) | O(n) | O(1) |
| Traverse | O(n) | O(n) | O(n) | O(1) |

---

## 3. LeetCode Practice Problems (Linked List)

Here are **15 important LeetCode problems** to practice:

1. [Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)  
2. [Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/)  
3. [Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)  
4. [Remove Linked List Elements](https://leetcode.com/problems/remove-linked-list-elements/)  
5. [Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list/)  
6. [Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/)  
7. [Intersection of Two Linked Lists](https://leetcode.com/problems/intersection-of-two-linked-lists/)  
8. [Add Two Numbers](https://leetcode.com/problems/add-two-numbers/)  
9. [Swap Nodes in Pairs](https://leetcode.com/problems/swap-nodes-in-pairs/)  
10. [Rotate List](https://leetcode.com/problems/rotate-list/)  
11. [Partition List](https://leetcode.com/problems/partition-list/)  
12. [Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)  
13. [Reorder List](https://leetcode.com/problems/reorder-list/)  
14. [Copy List with Random Pointer](https://leetcode.com/problems/copy-list-with-random-pointer/)  
15. [Flatten a Multilevel Doubly Linked List](https://leetcode.com/problems/flatten-a-multilevel-doubly-linked-list/)  

---

# Linked List – Code Review Practice (Medium Level)

Below are **15 buggy/inefficient code snippets** related to Linked Lists.  
Your task: **review, debug, and optimize them.**

---

### 1. Reverse a Linked List
**Description:** Reverse a singly linked list.  
**Input:** `1 -> 2 -> 3 -> 4`  
**Output:** `4 -> 3 -> 2 -> 1`  

```python
def reverse_list(head):
    prev = None
    while head:
        head.next = prev
        prev = head
    return prev
```

---

### 2. Find Middle Node
**Description:** Return the middle node.  
**Input:** `1 -> 2 -> 3 -> 4 -> 5`  
**Output:** `3`  

```python
def middle_node(head):
    slow = head
    fast = head
    while fast:
        slow = slow.next
        fast = fast.next.next
    return slow
```

---

### 3. Detect Cycle in Linked List
**Description:** Check if cycle exists.  
**Input:** `1 -> 2 -> 3 -> 4 -> 2 (cycle)`  
**Output:** `True`  

```python
def hasCycle(head):
    slow = head
    fast = head
    while fast:
        slow = slow.next
        fast = fast.next.next
        if slow == fast:
            return True
    return False
```

---

### 4. Merge Two Sorted Lists
**Description:** Merge two sorted lists into one.  
**Input:** `1->2->4`, `1->3->4`  
**Output:** `1->1->2->3->4->4`  

```python
def merge_lists(l1, l2):
    dummy = Node(0)
    curr = dummy
    while l1 and l2:
        if l1.val < l2.val:
            curr.next = l1
            l1 = l1.next
        else:
            curr.next = l2
            l2 = l2.next
    return dummy.next 
```

---

### 5. Remove Duplicates
**Description:** Remove duplicates from sorted list.  
**Input:** `1 -> 1 -> 2 -> 3 -> 3`  
**Output:** `1 -> 2 -> 3`  

```python
def remove_duplicates(head):
    curr = head
    while curr:
        if curr.val == curr.next.val:
            curr.next = curr.next.next
        curr = curr.next
    return head
```

---

### 6. Delete Node (given node reference)
**Description:** Delete node by reference.  
**Input:** `1 -> 2 -> 3`, delete `2`  
**Output:** `1 -> 3`  

```python
def deleteNode(node):
    node = node.next 
```

---

### 7. Add Two Numbers (Linked List)
**Description:** Add numbers represented by LL.  
**Input:** `(2 -> 4 -> 3) + (5 -> 6 -> 4)`  
**Output:** `7 -> 0 -> 8`  

```python
def add_two_numbers(l1, l2):
    carry = 0
    dummy = Node(0)
    curr = dummy
    while l1 or l2:
        s = l1.val + l2.val + carry
        carry = s // 10
        curr.next = Node(s % 10)
        curr = curr.next
        l1 = l1.next
        l2 = l2.next
    return dummy.next
```

---

### 8. Remove Nth Node from End
**Description:** Remove Nth node from end.  
**Input:** `1 -> 2 -> 3 -> 4 -> 5, n=2`  
**Output:** `1 -> 2 -> 3 -> 5`  

```python
def removeNthFromEnd(head, n):
    slow = head
    fast = head
    for i in range(n):
        fast = fast.next
    while fast:
        fast = fast.next
        slow = slow.next
    slow.next = slow.next.next
    return head
```

---

### 9. Palindrome Linked List
**Description:** Check if LL is palindrome.  
**Input:** `1 -> 2 -> 2 -> 1`  
**Output:** `True`  

```python
def is_palindrome(head):
    vals = []
    while head:
        vals.append(head.val)
        head = head.next
    return vals == vals.reverse()
```

---

### 10. Reorder List
**Description:** Reorder LL to alternate.  
**Input:** `1 -> 2 -> 3 -> 4`  
**Output:** `1 -> 4 -> 2 -> 3`  

```python
def reorder_list(head):
    if not head: return
    slow = head
    fast = head
    while fast:
        slow = slow.next
        fast = fast.next.next
    prev = None
    while slow:
        slow.next = prev
        prev = slow
        slow = slow.next 
    # merge missing
```

---

### 11. Rotate List
**Description:** Rotate right by k places.  
**Input:** `1 -> 2 -> 3 -> 4 -> 5, k=2`  
**Output:** `4 -> 5 -> 1 -> 2 -> 3`  

```python
def rotate_list(head, k):
    if not head: return None
    length = 0
    curr = head
    while curr:
        length += 1
        curr = curr.next
    k = k % length
    for i in range(k):
        curr = head
        while curr.next.next:
            curr = curr.next
        new_head = curr.next
        curr.next = None
        new_head.next = head
        head = new_head
    return head
```

---

### 12. Intersection of Two Linked Lists
**Description:** Find intersection node.  
**Input:** `List A: 4->1->8->4->5, List B: 5->6->1->8->4->5`  
**Output:** `8`  

```python
def getIntersectionNode(headA, headB):
    while headA != headB:
        headA = headA.next if headA else headB
        headB = headB.next if headB else headA
    return headA
```

---

### 13. Flatten Multilevel Doubly LL
**Description:** Flatten child nodes.  
**Input:** `1->2->3->null with child 4->5`  
**Output:** `1->2->3->4->5`  

```python
def flatten(head):
    if not head: return None
    curr = head
    while curr:
        if curr.child:
            temp = curr.next
            curr.next = curr.child
            curr.child = None
        curr = curr.next
    return head
```

---

### 14. Partition List
**Description:** Partition list by x.  
**Input:** `1->4->3->2->5->2, x=3`  
**Output:** `1->2->2->4->3->5`  

```python
def partition(head, x):
    before = Node(0)
    after = Node(0)
    while head:
        if head.val < x:
            before.next = head
        else:
            after.next = head
        head = head.next
    before.next = after
    return before.next
```

---

### 15. Copy List with Random Pointer
**Description:** Deep copy LL with random pointers.  
**Input:** `1->2 with random pointers`  
**Output:** Deep copy of same structure  

```python
def copyRandomList(head):
    if not head: return None
    mapping = {}
    curr = head
    while curr:
        mapping[curr] = Node(curr.val)
        curr = curr.next
    curr = head
    while curr:
        mapping[curr].next = mapping[curr.next]
        mapping[curr].random = mapping[curr.random]
        curr = curr.next
    return mapping[head]
```

