## 1. [Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)  
**Idea:** Iteratively reverse the `next` pointers.  

```python
class Solution:
    def reverseList(self, head):
        prev = None
        while head:
            nxt = head.next
            head.next = prev
            prev = head
            head = nxt
        return prev
```

---

## 2. [Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/)  
**Idea:** Use fast & slow pointers.  

```python
class Solution:
    def middleNode(self, head):
        slow, fast = head, head
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
        return slow
```

---

## 3. [Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)  
**Idea:** Two-pointer merge like in merge sort.  

```python
class Solution:
    def mergeTwoLists(self, l1, l2):
        dummy = tail = ListNode(0)
        while l1 and l2:
            if l1.val < l2.val:
                tail.next, l1 = l1, l1.next
            else:
                tail.next, l2 = l2, l2.next
            tail = tail.next
        tail.next = l1 or l2
        return dummy.next
```

---

## 4. [Remove Linked List Elements](https://leetcode.com/problems/remove-linked-list-elements/)  
**Idea:** Dummy node + iterate.  

```python
class Solution:
    def removeElements(self, head, val):
        dummy = ListNode(0, head)
        cur = dummy
        while cur.next:
            if cur.next.val == val:
                cur.next = cur.next.next
            else:
                cur = cur.next
        return dummy.next
```

---

## 5. [Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list/)  
**Idea:** Reverse 2nd half & compare.  

```python
class Solution:
    def isPalindrome(self, head):
        slow, fast = head, head
        while fast and fast.next:
            slow, fast = slow.next, fast.next.next
        prev = None
        while slow:
            nxt, slow.next, prev, slow = slow.next, prev, slow, slow.next
        while prev:
            if prev.val != head.val:
                return False
            prev, head = prev.next, head.next
        return True
```

---

## 6. [Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/)  
**Idea:** Floyd’s cycle detection.  

```python
class Solution:
    def hasCycle(self, head):
        slow = fast = head
        while fast and fast.next:
            slow, fast = slow.next, fast.next.next
            if slow == fast:
                return True
        return False
```

---

## 7. [Intersection of Two Linked Lists](https://leetcode.com/problems/intersection-of-two-linked-lists/)  
**Idea:** Two-pointer switching lists.  

```python
class Solution:
    def getIntersectionNode(self, headA, headB):
        if not headA or not headB: return None
        a, b = headA, headB
        while a != b:
            a = a.next if a else headB
            b = b.next if b else headA
        return a
```

---

## 8. [Add Two Numbers](https://leetcode.com/problems/add-two-numbers/)  
**Idea:** Simulate digit-by-digit addition.  

```python
class Solution:
    def addTwoNumbers(self, l1, l2):
        dummy = cur = ListNode(0)
        carry = 0
        while l1 or l2 or carry:
            v1, v2 = (l1.val if l1 else 0), (l2.val if l2 else 0)
            carry, out = divmod(v1 + v2 + carry, 10)
            cur.next = ListNode(out)
            cur = cur.next
            l1, l2 = (l1.next if l1 else None), (l2.next if l2 else None)
        return dummy.next
```

---

## 9. [Swap Nodes in Pairs](https://leetcode.com/problems/swap-nodes-in-pairs/)  

```python
class Solution:
    def swapPairs(self, head):
        dummy = prev = ListNode(0, head)
        while head and head.next:
            a, b = head, head.next
            prev.next, b.next, a.next = b, a, b.next
            prev, head = a, a.next
        return dummy.next
```

---

## 10. [Rotate List](https://leetcode.com/problems/rotate-list/)  

```python
class Solution:
    def rotateRight(self, head, k):
        if not head: return None
        n, tail = 1, head
        while tail.next:
            tail, n = tail.next, n + 1
        tail.next = head
        k %= n
        for _ in range(n - k):
            tail = tail.next
        res = tail.next
        tail.next = None
        return res
```

---

## 11. [Partition List](https://leetcode.com/problems/partition-list/)  

```python
class Solution:
    def partition(self, head, x):
        before = b = ListNode(0)
        after = a = ListNode(0)
        while head:
            if head.val < x:
                b.next, b = head, head
            else:
                a.next, a = head, head
            head = head.next
        a.next = None
        b.next = after.next
        return before.next
```

---

## 12. [Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)  

```python
class Solution:
    def removeNthFromEnd(self, head, n):
        dummy = first = second = ListNode(0, head)
        for _ in range(n+1):
            first = first.next
        while first:
            first, second = first.next, second.next
        second.next = second.next.next
        return dummy.next
```

---

## 13. [Reorder List](https://leetcode.com/problems/reorder-list/)  

```python
class Solution:
    def reorderList(self, head):
        if not head: return
        slow, fast = head, head
        while fast and fast.next:
            slow, fast = slow.next, fast.next.next
        prev = None
        while slow:
            nxt, slow.next, prev, slow = slow.next, prev, slow, slow.next
        first, second = head, prev
        while second.next:
            tmp1, tmp2 = first.next, second.next
            first.next, second.next = second, tmp1
            first, second = tmp1, tmp2
```

---

## 14. [Copy List with Random Pointer](https://leetcode.com/problems/copy-list-with-random-pointer/)  

```python
class Solution:
    def copyRandomList(self, head):
        if not head: return None
        cur = head
        while cur:
            nxt = cur.next
            cur.next = Node(cur.val, nxt)
            cur = nxt
        cur = head
        while cur:
            if cur.random:
                cur.next.random = cur.random.next
            cur = cur.next.next
        dummy, cur, copy = Node(0), head, None
        copy_cur = dummy
        while cur:
            copy = cur.next
            cur.next, copy_cur.next = copy.next, copy
            cur, copy_cur = cur.next, copy_cur.next
        return dummy.next
```

---

## 15. [Flatten a Multilevel Doubly Linked List](https://leetcode.com/problems/flatten-a-multilevel-doubly-linked-list/)  

```python
class Solution:
    def flatten(self, head):
        if not head: return head
        pseudoHead = Node(0, None, head, None)
        self.flattenDFS(pseudoHead, head)
        pseudoHead.next.prev = None
        return pseudoHead.next

    def flattenDFS(self, prev, curr):
        if not curr: return prev
        curr.prev = prev
        prev.next = curr
        tempNext = curr.next
        tail = self.flattenDFS(curr, curr.child)
        curr.child = None
        return self.flattenDFS(tail, tempNext)
```

