## 1. Two Sum
[Problem Link](https://leetcode.com/problems/two-sum/)

```python
# Import not needed here, just using dictionary
def twoSum(nums, target):
    hashmap = {}
    for i, num in enumerate(nums):
        if target - num in hashmap:
            return [hashmap[target - num], i]
        hashmap[num] = i
```

---

## 2. Valid Anagram
[Problem Link](https://leetcode.com/problems/valid-anagram/)

```python
# Import Counter for frequency comparison
from collections import Counter

def isAnagram(s, t):
    return Counter(s) == Counter(t)
```

---

## 3. Group Anagrams
[Problem Link](https://leetcode.com/problems/group-anagrams/)

```python
# Import defaultdict for grouping
from collections import defaultdict

def groupAnagrams(strs):
    groups = defaultdict(list)
    for word in strs:
        groups[tuple(sorted(word))].append(word)
    return list(groups.values())
```

---

## 4. Top K Frequent Elements
[Problem Link](https://leetcode.com/problems/top-k-frequent-elements/)

```python
# Import Counter for counting frequencies
from collections import Counter

def topKFrequent(nums, k):
    count = Counter(nums)
    return [num for num, _ in count.most_common(k)]
```

---

## 5. Subarray Sum Equals K
[Problem Link](https://leetcode.com/problems/subarray-sum-equals-k/)

```python
# Import not needed
def subarraySum(nums, k):
    count, curr_sum = 0, 0
    prefix = {0: 1}
    for num in nums:
        curr_sum += num
        count += prefix.get(curr_sum - k, 0)
        prefix[curr_sum] = prefix.get(curr_sum, 0) + 1
    return count
```

---

## 6. Intersection of Two Arrays
[Problem Link](https://leetcode.com/problems/intersection-of-two-arrays/)

```python
# Import not needed, just using set
def intersection(nums1, nums2):
    return list(set(nums1) & set(nums2))
```

---

## 7. Happy Number
[Problem Link](https://leetcode.com/problems/happy-number/)

```python
# Import not needed
def isHappy(n):
    seen = set()
    while n != 1 and n not in seen:
        seen.add(n)
        n = sum(int(d)**2 for d in str(n))
    return n == 1
```

---

## 8. Word Pattern
[Problem Link](https://leetcode.com/problems/word-pattern/)

```python
# Import not needed
def wordPattern(pattern, s):
    words = s.split()
    if len(words) != len(pattern):
        return False
    mapping = {}
    reverse = {}
    for c, w in zip(pattern, words):
        if mapping.get(c, w) != w or reverse.get(w, c) != c:
            return False
        mapping[c] = w
        reverse[w] = c
    return True
```

---

## 9. Isomorphic Strings
[Problem Link](https://leetcode.com/problems/isomorphic-strings/)

```python
# Import not needed
def isIsomorphic(s, t):
    map_s, map_t = {}, {}
    for i, c in enumerate(s):
        if map_s.get(c, t[i]) != t[i] or map_t.get(t[i], c) != c:
            return False
        map_s[c] = t[i]
        map_t[t[i]] = c
    return True
```

---

## 10. Minimum Index Sum of Two Lists
[Problem Link](https://leetcode.com/problems/minimum-index-sum-of-two-lists/)

```python
# Import not needed
def findRestaurant(list1, list2):
    index_map = {val: i for i, val in enumerate(list1)}
    min_sum = float('inf')
    res = []
    for j, val in enumerate(list2):
        if val in index_map:
            s = j + index_map[val]
            if s < min_sum:
                min_sum, res = s, [val]
            elif s == min_sum:
                res.append(val)
    return res
```

---

## 11. Longest Substring Without Repeating Characters
[Problem Link](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

```python
# Import not needed
def lengthOfLongestSubstring(s):
    seen, start, max_len = {}, 0, 0
    for i, c in enumerate(s):
        if c in seen and seen[c] >= start:
            start = seen[c] + 1
        seen[c] = i
        max_len = max(max_len, i - start + 1)
    return max_len
```

---

## 12. First Unique Character in a String
[Problem Link](https://leetcode.com/problems/first-unique-character-in-a-string/)

```python
# Import Counter for counting
from collections import Counter

def firstUniqChar(s):
    count = Counter(s)
    for i, c in enumerate(s):
        if count[c] == 1:
            return i
    return -1
```

---

## 13. Contains Duplicate II
[Problem Link](https://leetcode.com/problems/contains-duplicate-ii/)

```python
# Import not needed
def containsNearbyDuplicate(nums, k):
    seen = {}
    for i, num in enumerate(nums):
        if num in seen and i - seen[num] <= k:
            return True
        seen[num] = i
    return False
```

---

## 14. Find Duplicate Subtrees
[Problem Link](https://leetcode.com/problems/find-duplicate-subtrees/)

```python
# Import defaultdict for serialization mapping
from collections import defaultdict

class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right

def findDuplicateSubtrees(root):
    count = defaultdict(int)
    res = []

    def serialize(node):
        if not node:
            return "#"
        serial = f"{node.val},{serialize(node.left)},{serialize(node.right)}"
        count[serial] += 1
        if count[serial] == 2:
            res.append(node)
        return serial

    serialize(root)
    return res
```

---

## 15. Alien Dictionary
[Problem Link](https://leetcode.com/problems/alien-dictionary/)

```python
# Import defaultdict and deque for graph + BFS topological sort
from collections import defaultdict, deque

def alienOrder(words):
    graph = defaultdict(set)
    indegree = {c: 0 for word in words for c in word}

    for i in range(len(words) - 1):
        w1, w2 = words[i], words[i+1]
        if len(w1) > len(w2) and w1.startswith(w2):
            return ""
        for c1, c2 in zip(w1, w2):
            if c1 != c2:
                if c2 not in graph[c1]:
                    graph[c1].add(c2)
                    indegree[c2] += 1
                break

    queue = deque([c for c in indegree if indegree[c] == 0])
    order = []
    while queue:
        c = queue.popleft()
        order.append(c)
        for nei in graph[c]:
            indegree[nei] -= 1
            if indegree[nei] == 0:
                queue.append(nei)

    return "".join(order) if len(order) == len(indegree) else ""
```

---

## 16. Continuous Subarray Sum
[Problem Link](https://leetcode.com/problems/continuous-subarray-sum/)

```python
# Import not needed
def checkSubarraySum(nums, k):
    prefix = {0: -1}
    total = 0
    for i, num in enumerate(nums):
        total += num
        if k != 0:
            total %= k
        if total in prefix:
            if i - prefix[total] > 1:
                return True
        else:
            prefix[total] = i
    return False
```
