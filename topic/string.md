# Strings Learning Path in Python

## 1. Introduction to Strings
Strings are sequences of characters enclosed in single quotes (' '), double quotes (" "), or triple quotes (''' ''' or """ """).
They are **immutable** in Python, meaning once created, they cannot be modified in place.

Example:
```python
s = "hello"
print(s[0])  # Output: h
print(len(s))  # Output: 5
```

---

## 2. Common Operations on Strings

### 2.1 Accessing Characters
```python
s = "python"
print(s[0])   # 'p'
print(s[-1])  # 'n'
```

### 2.2 String Slicing
```python
s = "programming"
print(s[0:6])   # 'progra'
print(s[3:])    # 'gramming'
print(s[:5])    # 'progr'
```

### 2.3 String Concatenation & Repetition
```python
a = "Hello"
b = "World"
print(a + " " + b)   # "Hello World"
print(a * 3)         # "HelloHelloHello"
```

### 2.4 Checking Substrings
```python
s = "learning python"
print("python" in s)   # True
print("java" not in s) # True
```

### 2.5 Useful String Methods
```python
s = "  Avenger END  "
print(s.lower())       # '  avenger end  '
print(s.upper())       # '  AVENGER END  '
print(s.strip())       # 'Avenger END'
print(s.replace("END", "End"))  # '  Avenger End  '
print(s.split())       # ['Avenger', 'END']
```

### 2.6 Joining Strings
```python
words = ["Python", "is", "fun"]
print(" ".join(words))   # "Python is fun"
```

### 2.7 Reversing Strings
```python
s = "hello"
print(s[::-1])  # "olleh"
```

---

## 3. LeetCode Practice Problems (String)

1. [Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)
2. [Reverse String](https://leetcode.com/problems/reverse-string/)
3. [Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/)
4. [Implement strStr()](https://leetcode.com/problems/implement-strstr/)
5. [Valid Anagram](https://leetcode.com/problems/valid-anagram/)
6. [Count and Say](https://leetcode.com/problems/count-and-say/)
7. [First Unique Character in a String](https://leetcode.com/problems/first-unique-character-in-a-string/)
8. [Group Anagrams](https://leetcode.com/problems/group-anagrams/)
9. [Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/)
10. [String to Integer (atoi)](https://leetcode.com/problems/string-to-integer-atoi/)
11. [Zigzag Conversion](https://leetcode.com/problems/zigzag-conversion/)
12. [Multiply Strings](https://leetcode.com/problems/multiply-strings/)
13. [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)
14. [Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/)
15. [Decode Ways](https://leetcode.com/problems/decode-ways/)

---

## 4. String – Code Review Practice (Medium Level)

Below are **15 buggy/inefficient code snippets** related to strings.  
Your task is to **review, debug, and optimize them**.

---

### 1. Reverse a String
**Description:** Reverse the characters in a string.  
**Input:** "hello"  
**Output:** "olleh"  

```python
def reverse_string(s):
    res = ""
    for i in range(len(s)):
        res += s[i]   # inefficient: string concatenation in loop
    return res
```

---

### 2. Check Palindrome
**Description:** Check if a string is palindrome ignoring case.  
**Input:** "Madam"  
**Output:** True  

```python
def is_palindrome(s):
    s = s.lower()
    return s == s[::-2]   # bug: slicing step wrong
```

---

### 3. Count Vowels
**Description:** Count how many vowels are in the string.  
**Input:** "education"  
**Output:** 5  

```python
def count_vowels(s):
    vowels = "aeiou"
    count = 0
    for ch in s:
        if ch in vowels:
            count += 1
    return count / len(s)   # bug: should return count, not ratio
```

---

### 4. Remove Duplicates
**Description:** Remove duplicate characters but preserve order.  
**Input:** "programming"  
**Output:** "progamin"  

```python
def remove_duplicates(s):
    return "".join(set(s))   # bug: order is not preserved
```

---

### 5. First Unique Character
**Description:** Return index of first non-repeating character.  
**Input:** "leetcode"  
**Output:** 0  

```python
def first_unique_char(s):
    for i in range(len(s)):
        if s.count(s[i]) == 1:   # inefficient: O(n^2)
            return i
    return -1
```

---

### 6. Anagram Check
**Description:** Check if two strings are anagrams.  
**Input:** "listen", "silent"  
**Output:** True  

```python
def is_anagram(s, t):
    return sorted(s) == sorted(t)   # works but inefficient for very large strings
```

---

### 7. String Compression
**Description:** Compress consecutive repeating characters.  
**Input:** "aaabbc"  
**Output:** "a3b2c1"  

```python
def compress(s):
    result = ""
    count = 1
    for i in range(1, len(s)):
        if s[i] == s[i-1]:
            count += 1
        else:
            result += s[i-1] + str(count)
            count = 1
    return result   # bug: missing last character
```

---

### 8. Word Reversal
**Description:** Reverse order of words in a sentence.  
**Input:** "hello world"  
**Output:** "world hello"  

```python
def reverse_words(s):
    words = s.split(" ")
    return " ".join(words[::-1]).strip()  # bug: strip removes valid spaces
```

---

### 9. Check Rotation
**Description:** Check if s2 is a rotation of s1.  
**Input:** "abcde", "cdeab"  
**Output:** True  

```python
def is_rotation(s1, s2):
    return s2 in (s1 + s1)   # works but missing length check
```

---

### 10. Substring Search
**Description:** Find index of first occurrence of a pattern.  
**Input:** "hello", "ll"  
**Output:** 2  

```python
def find_substring(s, pattern):
    for i in range(len(s)):
        if s[i:i+len(pattern)] == pattern:
            return i
    return 1   # bug: should return -1 if not found
```

---

### 11. Longest Word
**Description:** Return the longest word from a sentence.  
**Input:** "I love programming"  
**Output:** "programming"  

```python
def longest_word(s):
    words = s.split()
    longest = ""
    for w in words:
        if len(w) > len(longest):
            longest = w
    return len(longest)   # bug: returns length instead of word
```

---

### 12. Remove Spaces
**Description:** Remove all whitespace from the string.  
**Input:** "a b\tc\n"  
**Output:** "abc"  

```python
def remove_spaces(s):
    return s.replace(" ", "")   # bug: only removes spaces, not tabs/newlines
```

---

### 13. Character Frequency
**Description:** Count frequency of each character.  
**Input:** "banana"  
**Output:** {'b':1, 'a':3, 'n':2}  

```python
def char_frequency(s):
    freq = {}
    for ch in s:
        freq[ch] =+ 1   # bug: should be +=
    return freq
```

---

### 14. Title Case
**Description:** Convert string into title case (capitalize each word).  
**Input:** "hello world"  
**Output:** "Hello World"  

```python
def to_title_case(s):
    return " ".join([word.capitalize for word in s.split()])   # bug: missing ()
```

---

### 15. Valid Parentheses
**Description:** Check if the parentheses/brackets/braces are valid.  
**Input:** "()[]{}"  
**Output:** True  

```python
def is_valid_parentheses(s):
    stack = []
    mapping = {')':'(', ']':'[', '}':'{'}
    for ch in s:
        if ch in mapping:
            top = stack.pop()   # bug: may pop from empty list
            if mapping[ch] != top:
                return False
        else:
            stack.append(ch)
    return True   # bug: should check stack is empty
```
