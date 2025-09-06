# Set

## 1. Introduction to Set

In Python, a **set** is an unordered collection of unique elements.  
- It does not allow duplicate values.  
- Elements must be **hashable** (immutable types like int, str, tuple).  
- Commonly used for **membership tests**, removing duplicates, and set operations (union, intersection, difference).

Example:
```python
s = {1, 2, 3, 3}
print(s)  # {1, 2, 3}
print(2 in s)  # True
```

---

## 2. Common Operations on Set

| Operation | Average Time Complexity | Worst Case | Space Complexity |
|-----------|--------------------------|------------|------------------|
| Insert (add) | O(1) | O(n) | O(n) |
| Delete (remove/discard) | O(1) | O(n) | O(n) |
| Search (in) | O(1) | O(n) | O(1) |
| Union | O(len(s1) + len(s2)) | O(len(s1) * len(s2)) | O(n) |
| Intersection | O(min(len(s1), len(s2))) | O(len(s1) * len(s2)) | O(n) |
| Difference | O(len(s1)) | O(len(s1)) | O(n) |

---

# LeetCode Practice Problems (Sets)

(Easy → Medium) to strengthen `set` skills in Python:

1. [Contains Duplicate](https://leetcode.com/problems/contains-duplicate/)  
2. [Intersection of Two Arrays](https://leetcode.com/problems/intersection-of-two-arrays/)  
3. [Happy Number](https://leetcode.com/problems/happy-number/)  
4. [Valid Sudoku](https://leetcode.com/problems/valid-sudoku/)  
5. [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)  
6. [Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence/)  
7. [Unique Email Addresses](https://leetcode.com/problems/unique-email-addresses/)  
8. [Intersection of Two Linked Lists](https://leetcode.com/problems/intersection-of-two-linked-lists/)  
9. [Minimum Index Sum of Two Lists](https://leetcode.com/problems/minimum-index-sum-of-two-lists/)  
10. [Number of Distinct Islands](https://leetcode.com/problems/number-of-distinct-islands/)  
11. [Fair Candy Swap](https://leetcode.com/problems/fair-candy-swap/)  
12. [Unique Morse Code Words](https://leetcode.com/problems/unique-morse-code-words/)  
13. [Most Common Word](https://leetcode.com/problems/most-common-word/)  
14. [Intersection of Multiple Arrays](https://leetcode.com/problems/intersection-of-multiple-arrays/)  
15. [First Missing Positive](https://leetcode.com/problems/first-missing-positive/)  


---