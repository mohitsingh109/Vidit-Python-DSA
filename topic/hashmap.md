# Hash Map (dict in Python) Learning Path

## 1. Introduction to Hash Map

- A **Hash Map** (dictionary in Python) stores data in **key-value pairs**.
- Keys must be **unique** and **hashable** (immutable types like `int`, `str`, `tuple`).
- Values can be any type (mutable or immutable).
- Hash Maps use a **hashing function** to provide **average O(1) access time** for lookups, insertions, and deletions.
- Python’s `dict` is implemented as a **hash table** with open addressing.

Example:
```python
student = {"name": "Alice", "age": 21, "grade": "A"}
print(student["name"])   # Alice
student["age"] = 22      # update
student["city"] = "NYC"  # insert new key
```

---

## 2. Common Operations on Hash Map

| Operation               | Average Time Complexity | Worst Case | Space Complexity |
|--------------------------|-------------------------|------------|------------------|
| Insert / Update key      | O(1)                   | O(n)       | O(n)             |
| Delete key               | O(1)                   | O(n)       | O(n)             |
| Access (lookup by key)   | O(1)                   | O(n)       | O(n)             |
| Check if key exists      | O(1)                   | O(n)       | O(n)             |
| Iterate over keys/values | O(n)                   | O(n)       | O(n)             |

---

## 3. LeetCode Practice Problems (Hash Map)

1. [Two Sum](https://leetcode.com/problems/two-sum/)
2. [Valid Anagram](https://leetcode.com/problems/valid-anagram/)
3. [Group Anagrams](https://leetcode.com/problems/group-anagrams/)
4. [Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/)
5. [Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/)
6. [Intersection of Two Arrays](https://leetcode.com/problems/intersection-of-two-arrays/)
7. [Happy Number](https://leetcode.com/problems/happy-number/)
8. [Word Pattern](https://leetcode.com/problems/word-pattern/)
9. [Isomorphic Strings](https://leetcode.com/problems/isomorphic-strings/)
10. [Minimum Index Sum of Two Lists](https://leetcode.com/problems/minimum-index-sum-of-two-lists/)
11. [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)
12. [First Unique Character in a String](https://leetcode.com/problems/first-unique-character-in-a-string/)
13. [Contains Duplicate II](https://leetcode.com/problems/contains-duplicate-ii/)
14. [Find Duplicate Subtrees](https://leetcode.com/problems/find-duplicate-subtrees/)
15. [Alien Dictionary](https://leetcode.com/problems/alien-dictionary/)
16. [Continuous Subarray Sum](https://leetcode.com/problems/continuous-subarray-sum/description/?utm_source=chatgpt.com)

---

## 4. Hash Map – Code Review Practice (Medium Level)

Below are **15 buggy/inefficient code snippets** related to hash maps.
Your task is to **review, debug, and optimize them**.

---

### 1. Count Word Frequencies
**Description:** Count frequency of each word in a sentence.  
**Input:** `"the cat and the dog"`  
**Output:** `{"the":2, "cat":1, "and":1, "dog":1}`  

```python
def word_count(sentence):
    words = sentence.split()
    freq = {}
    for w in words:
        freq[w] = 1
    return freq
```

---

### 2. Most Common Character
**Description:** Find most frequent character.  
**Input:** `"banana"`  
**Output:** `'a'`  

```python
def most_common_char(s):
    freq = {}
    for ch in s:
        freq[ch] = 1 
    return max(freq.keys()) 
```

---

### 3. Invert Dictionary
**Description:** Invert keys and values of dictionary.  
**Input:** `{"a":1,"b":2,"c":1}`  
**Output:** `{1:["a","c"], 2:["b"]}`  

```python
def invert_dict(d):
    inv = {}
    for k,v in d.items():
        inv[v] = k  
    return inv
```

---

### 4. Find Non-Repeated Words
**Description:** Return words appearing exactly once.  
**Input:** `"apple banana apple orange"`  
**Output:** `["banana","orange"]`  

```python
def unique_words(s):
    words = s.split()
    freq = {}
    for w in words:
        freq[w] = freq.get(w,0)+1
    return [k for k in freq if freq[k]<1]  
```

---

### 5. Check if Two Dicts Are Equal (ignoring order)
**Description:** Return True if dicts equal.  
**Input:** `{ "a":1, "b":2 }, { "b":2, "a":1 }`  
**Output:** `True`  

```python
def dict_equal(d1, d2):
    return d1.items() == d2.items()  
```

---

### 6. Find First Repeated Character
**Description:** Find first character that repeats.  
**Input:** `"swiss"`  
**Output:** `'s'`  

```python
def first_repeated_char(s):
    seen = {}
    for ch in s:
        if ch in seen:
            return ch
        else:
            seen[ch] = True
    return None
```

---

### 7. Find Key with Minimum Value
**Description:** Return key having the smallest value.  
**Input:** `{"a":3,"b":1,"c":2}`  
**Output:** `"b"`  

```python
def min_key(d):
    return min(d) 
```

---

### 8. Merge Two Dictionaries (sum values for same keys)
**Description:** Merge dictionaries.  
**Input:** `{"a":1,"b":2}, {"b":3,"c":4}`  
**Output:** `{"a":1,"b":5,"c":4}`  

```python
def merge_dicts(d1, d2):
    res = d1
    for k,v in d2.items():
        res[k] = v 
    return res
```

---

### 9. Find Most Common Word (ignoring case)
**Description:** Return most frequent word ignoring case.  
**Input:** `"Apple apple banana"`  
**Output:** `"apple"`  

```python
def most_common_word(s):
    words = s.split()
    freq = {}
    for w in words:
        freq[w] = freq.get(w,0)+1
    return max(freq, key=len) 
```

---

### 10. Frequency of Characters in Two Strings
**Description:** Compare if two strings have same char frequencies.  
**Input:** `"abc", "bca"`  
**Output:** True  

```python
def same_char_freq(s1, s2):
    return set(s1) == set(s2)
```

---

### 11. Remove Keys with Value Below Threshold
**Description:** Remove keys where value < threshold.  
**Input:** `{"a":5,"b":2,"c":7}, threshold=3`  
**Output:** `{"a":5,"c":7}`  

```python
def remove_below(d, t):
    for k,v in d.items():
        if v < t:
            d.pop(k)
    return d
```

---

### 12. Find Longest Word by Frequency
**Description:** Find longest word among those with highest frequency.  
**Input:** `"dog cat cat dog dog bat"`  
**Output:** `"dog"`  

```python
def longest_frequent_word(s):
    words = s.split()
    freq = {}
    for w in words:
        freq[w] = freq.get(w,0)+1
    max_freq = max(freq.values())
    return max([k for k,v in freq.items() if v==max_freq]) 
```

---

### 13. Check If Dictionary Is Subset
**Description:** Check if d1 is subset of d2.  
**Input:** `{"a":1}, {"a":1,"b":2}`  
**Output:** True  

```python
def is_subset(d1, d2):
    return set(d1.keys()).issubset(set(d2.keys())) 
```

---

### 14. Find First Unique Word
**Description:** Return first word that appears once.  
**Input:** `"this is a test this is fun"`  
**Output:** `"a"`  

```python
def first_unique_word(s):
    words = s.split()
    freq = {}
    for w in words:
        freq[w] = freq.get(w,0)+1
    for w in freq: 
        if freq[w]==1:
            return w
    return None
```

---

### 15. Reverse Dictionary Lookup
**Description:** Return list of keys mapping to given value.  
**Input:** `{"a":1,"b":2,"c":1}, val=1`  
**Output:** `["a","c"]`  

```python
def reverse_lookup(d, val):
    for k,v in d.items():
        if v == val:
            return [k]  
    return []
```
