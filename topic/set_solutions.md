
## 1. [Contains Duplicate](https://leetcode.com/problems/contains-duplicate/)

```python
class Solution:
    def containsDuplicate(self, nums):
        return len(nums) != len(set(nums))
```

---

## 2. [Intersection of Two Arrays](https://leetcode.com/problems/intersection-of-two-arrays/)

```python
class Solution:
    def intersection(self, nums1, nums2):
        return list(set(nums1) & set(nums2))
```

---

## 3. [Happy Number](https://leetcode.com/problems/happy-number/)

```python
class Solution:
    def isHappy(self, n: int) -> bool:
        seen = set()
        while n != 1 and n not in seen:
            seen.add(n)
            n = sum(int(c) ** 2 for c in str(n))
        return n == 1
```

---

## 4. [Valid Sudoku](https://leetcode.com/problems/valid-sudoku/)

```python
class Solution:
    def isValidSudoku(self, board):
        rows = [set() for _ in range(9)]
        cols = [set() for _ in range(9)]
        boxes = [set() for _ in range(9)]
        for r in range(9):
            for c in range(9):
                val = board[r][c]
                if val == ".": continue
                if val in rows[r] or val in cols[c] or val in boxes[(r//3)*3 + c//3]:
                    return False
                rows[r].add(val)
                cols[c].add(val)
                boxes[(r//3)*3 + c//3].add(val)
        return True
```

---

## 5. [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        seen, left, res = set(), 0, 0
        for right, ch in enumerate(s):
            while ch in seen:
                seen.remove(s[left])
                left += 1
            seen.add(ch)
            res = max(res, right - left + 1)
        return res
```

---

## 6. [Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence/)

```python
class Solution:
    def longestConsecutive(self, nums):
        num_set, longest = set(nums), 0
        for n in num_set:
            if n - 1 not in num_set:
                length = 1
                while n + length in num_set:
                    length += 1
                longest = max(longest, length)
        return longest
```

---

## 7. [Unique Email Addresses](https://leetcode.com/problems/unique-email-addresses/)

```python
class Solution:
    def numUniqueEmails(self, emails):
        seen = set()
        for email in emails:
            local, domain = email.split("@")
            local = local.split("+")[0].replace(".", "")
            seen.add(local + "@" + domain)
        return len(seen)
```

---

## 8. [Intersection of Two Linked Lists](https://leetcode.com/problems/intersection-of-two-linked-lists/)

```python
class Solution:
    def getIntersectionNode(self, headA, headB):
        seen = set()
        while headA:
            seen.add(headA)
            headA = headA.next
        while headB:
            if headB in seen:
                return headB
            headB = headB.next
        return None
```

---

## 9. [Minimum Index Sum of Two Lists](https://leetcode.com/problems/minimum-index-sum-of-two-lists/)

```python
class Solution:
    def findRestaurant(self, list1, list2):
        index = {v: i for i, v in enumerate(list1)}
        res, min_sum = [], float("inf")
        for j, v in enumerate(list2):
            if v in index:
                s = j + index[v]
                if s < min_sum:
                    res, min_sum = [v], s
                elif s == min_sum:
                    res.append(v)
        return res
```

---

## 10. [Number of Distinct Islands](https://leetcode.com/problems/number-of-distinct-islands/)

```python
class Solution:
    def numDistinctIslands(self, grid):
        rows, cols = len(grid), len(grid[0])
        seen = set()

        def dfs(r, c, path, direction):
            if r < 0 or c < 0 or r >= rows or c >= cols or grid[r][c] == 0:
                return
            grid[r][c] = 0
            path.append(direction)
            dfs(r+1, c, path, "D")
            dfs(r-1, c, path, "U")
            dfs(r, c+1, path, "R")
            dfs(r, c-1, path, "L")
            path.append("B")

        for r in range(rows):
            for c in range(cols):
                if grid[r][c] == 1:
                    path = []
                    dfs(r, c, path, "S")
                    seen.add(tuple(path))
        return len(seen)
```

---

## 11. [Fair Candy Swap](https://leetcode.com/problems/fair-candy-swap/)

```python
class Solution:
    def fairCandySwap(self, A, B):
        setA, setB = set(A), set(B)
        diff = (sum(A) - sum(B)) // 2
        for a in setA:
            if a - diff in setB:
                return [a, a - diff]
```

---

## 12. [Unique Morse Code Words](https://leetcode.com/problems/unique-morse-code-words/)

```python
class Solution:
    def uniqueMorseRepresentations(self, words):
        codes = [".-","-...","-.-.","-..",".","..-.","--.","....","..",".---",
                 "-.-",".-..","--","-.","---",".--.","--.-",".-.","...","-",
                 "..-","...-",".--","-..-","-.--","--.."]
        seen = set()
        for w in words:
            seen.add("".join(codes[ord(c)-97] for c in w))
        return len(seen)
```

---

## 13. [Most Common Word](https://leetcode.com/problems/most-common-word/)

```python
import re
from collections import Counter

class Solution:
    def mostCommonWord(self, paragraph, banned):
        words = re.findall(r"\w+", paragraph.lower())
        banned_set = set(banned)
        counts = Counter(w for w in words if w not in banned_set)
        return counts.most_common(1)[0][0]
```

---

## 14. [Intersection of Multiple Arrays](https://leetcode.com/problems/intersection-of-multiple-arrays/)

```python
class Solution:
    def intersection(self, nums):
        res = set(nums[0])
        for arr in nums[1:]:
            res &= set(arr)
        return sorted(res)
```

---

## 15. [First Missing Positive](https://leetcode.com/problems/first-missing-positive/)

```python
class Solution:
    def firstMissingPositive(self, nums):
        n = len(nums)
        for i in range(n):
            while 1 <= nums[i] <= n and nums[nums[i]-1] != nums[i]:
                nums[nums[i]-1], nums[i] = nums[i], nums[nums[i]-1]
        for i in range(n):
            if nums[i] != i+1:
                return i+1
        return n+1
```

---
