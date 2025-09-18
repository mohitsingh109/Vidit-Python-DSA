# LeetCode Patterns – Hint
---

## BFS
1. **Binary Tree Level Order Traversal (#102)** – Use queue for level-order traversal.
2. **Binary Tree Level Order Traversal II (#107)** – Same as above, reverse at end.
3. **Binary Tree Zigzag Level Order Traversal (#103)** – Queue + alternating order per level.
4. **Binary Tree Right Side View (#199)** – BFS, take last element at each level.
5. **Minimum Depth of Binary Tree (#111)** – BFS, return depth of first leaf.
6. **Average of Levels in Binary Tree (#637)** – BFS, compute average per level.

---

## DFS
1. **Maximum Depth of Binary Tree (#104)** – Recursively explore left/right.
2. **Path Sum (#112)** – DFS check if root-to-leaf sum exists.
3. **Path Sum II (#113)** – DFS + backtracking to collect all valid paths.
4. **Diameter of Binary Tree (#543)** – DFS track max left+right path.
5. **Balanced Binary Tree (#110)** – DFS returns height, check balance.
6. **Subtree of Another Tree (#572)** – DFS compare subtrees.

---

## Two Pointers
1. **Valid Palindrome (#125)** – Left/right pointers skipping non-alphanumeric.
2. **Two Sum II (#167)** – Sorted array, two-pointer approach.
3. **Remove Duplicates from Sorted Array (#26)** – Slow/fast pointer.
4. **Move Zeroes (#283)** – Two pointers to swap non-zero elements.
5. **Reverse String (#344)** – Swap start and end pointers.
6. **Container With Most Water (#11)** – Two pointers inward, maximize area.

---

## Greedy
1. **Assign Cookies (#455)** – Sort and assign greedily.
2. **Lemonade Change (#860)** – Track $5/$10 bills greedily.
3. **Best Time to Buy and Sell Stock II (#122)** – Greedy accumulate profits.
4. **Non-overlapping Intervals (#435)** – Sort by end, greedily remove overlaps.
5. **Is Subsequence (#392)** – Greedy match characters.
6. **Jump Game (#55)** – Track furthest index reachable.

---

## Hash Table
1. **Two Sum (#1)** – HashMap for complement.
2. **Group Anagrams (#49)** – HashMap of sorted string / char count.
3. **Happy Number (#202)** – Detect cycle with HashSet.
4. **First Unique Character in a String (#387)** – Count frequencies.
5. **Valid Anagram (#242)** – Count characters in HashMap.
6. **Subarray Sum Equals K (#560)** – Prefix sum + HashMap count.

---

## HashSet
1. **Contains Duplicate (#217)** – Track seen numbers.
2. **Intersection of Two Arrays (#349)** – Use set intersection.
3. **Longest Consecutive Sequence (#128)** – Set + expand sequence.
4. **Happy Number (#202)** – Detect cycle.
5. **Missing Number (#268)** – Compare with full set.
6. **Contains Duplicate II (#219)** – HashSet sliding window.

---

## String
1. **Valid Parentheses (#20)** – Stack check.
2. **Implement strStr (#28)** – Substring search.
3. **Longest Common Prefix (#14)** – Compare prefixes.
4. **Reverse Words in a String (#151)** – Split, reverse, join.
5. **Length of Last Word (#58)** – Trim and count last word.
6. **Add Binary (#67)** – Simulate binary addition.

---

## Stack
1. **Min Stack (#155)** – Track stack with min values.
2. **Valid Parentheses (#20)** – Stack for brackets.
3. **Daily Temperatures (#739)** – Monotonic stack.
4. **Next Greater Element I (#496)** – Monotonic stack + map.
5. **Evaluate Reverse Polish Notation (#150)** – Stack evaluate.
6. **Backspace String Compare (#844)** – Simulate stack typing.

---

## Queue
1. **Implement Queue using Stacks (#232)** – Two stacks simulate queue.
2. **Number of Recent Calls (#933)** – Queue of timestamps.
3. **Design Circular Queue (#622)** – Array-based circular queue.
4. **Moving Average from Data Stream (#346)** – Queue sliding window.
5. **Open the Lock (#752)** – BFS with queue.
6. **Rotting Oranges (#994)** – BFS with queue.

---

## Sliding Window
1. **Longest Substring Without Repeating Characters (#3)** – Expand/shrink window.
2. **Minimum Size Subarray Sum (#209)** – Shrink window when sum >= target.
3. **Permutation in String (#567)** – Sliding window with char counts.
4. **Find All Anagrams in a String (#438)** – Sliding window + compare counts.
5. **Maximum Average Subarray I (#643)** – Fixed-size sliding window.
6. **Longest Repeating Character Replacement (#424)** – Sliding window + count.

---

## Prefix Sum
1. **Range Sum Query - Immutable (#303)** – Precompute prefix sums.
2. **Range Sum Query 2D - Immutable (#304)** – 2D prefix sums.
3. **Subarray Sum Equals K (#560)** – Prefix sum + map.
4. **Maximum Size Subarray Sum Equals k (#325)** – Prefix sum + map.
5. **Continuous Subarray Sum (#523)** – Prefix sum % k + map.
6. **Find Pivot Index (#724)** – Prefix sum left/right balance.

---

## Binary Search on Answer
1. **Koko Eating Bananas (#875)** – Binary search on eating speed.
2. **Find the Smallest Divisor Given a Threshold (#1283)** – Binary search divisor.
3. **Capacity To Ship Packages Within D Days (#1011)** – Binary search capacity.
4. **Split Array Largest Sum (#410)** – Binary search max subarray sum.
5. **Median of Two Sorted Arrays (#4)** – Binary search partition.
6. **Search in Rotated Sorted Array (#33)** – Modified binary search.

---
