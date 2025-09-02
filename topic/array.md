# Arrays

## Introduction to Arrays

An **array** is a collection of elements stored at contiguous memory locations.  
In Python, the closest structure is a **list**.

### Common Operations on Arrays (Lists in Python)

| Operation | Average Time Complexity | Worst Case | Space Complexity |
|-----------|--------------------------|-------------|------------------|
| Access (arr[i]) | O(1) | O(1) | O(1) |
| Update (arr[i] = x) | O(1) | O(1) | O(1) |
| Insert at end (append) | O(1) amortized | O(n) | O(1) |
| Insert at beginning | O(n) | O(n) | O(1) |
| Insert at middle | O(n) | O(n) | O(1) |
| Delete from end (pop) | O(1) | O(1) | O(1) |
| Delete from beginning | O(n) | O(n) | O(1) |
| Search (unsorted) | O(n) | O(n) | O(1) |
| Search (sorted, binary search) | O(log n) | O(log n) | O(1) |

---

## LeetCode Practice Problems (Arrays)

(Easy → Medium) to strengthen array skills:

1. [Two Sum](https://leetcode.com/problems/two-sum/)  
2. [Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)  
3. [Contains Duplicate](https://leetcode.com/problems/contains-duplicate/)  
4. [Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/)  
5. [Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)  
6. [Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/)  
7. [Majority Element](https://leetcode.com/problems/majority-element/)  
8. [Rotate Array](https://leetcode.com/problems/rotate-array/)  
9. [Intersection of Two Arrays II](https://leetcode.com/problems/intersection-of-two-arrays-ii/)  
10. [Move Zeroes](https://leetcode.com/problems/move-zeroes/)  
11. [Find All Numbers Disappeared in an Array](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/)  
12. [Third Maximum Number](https://leetcode.com/problems/third-maximum-number/)  
13. [Reshape the Matrix](https://leetcode.com/problems/reshape-the-matrix/)  
14. [Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/)  
15. [Container With Most Water](https://leetcode.com/problems/container-with-most-water/)  

---

# Arrays – Code Review Practice (Medium Level)

1. Identify **bugs**.  
2. Improve **efficiency**.  
3. Consider **usability and readability**.  
4. Think about **scalability and future augmentation**.  
5. State the **time and space complexity** after fixing.  

---

## 1. Subarray Sum Equals K

Description:
You are given an integer array nums and an integer k. Find the total number of continuous subarrays whose sum equals to k.
```python
def subarray_sum(nums, k):
    count = 0
    for i in range(len(nums)):
        s = 0
        for j in range(i, len(nums)):
            s += nums[j]
            if s == k:
                count += 1
    return count
```
Sample Input/Output:
`
nums = [1, 2, 3]
k = 3
Subarrays = [1,2], [3] → Output: 2
`


---

## 2. Rotate Array by K Steps
Description:
Rotate the array to the right by k steps.

```python
def rotate(nums, k):
    for _ in range(k):
        temp = nums.pop()
        nums.insert(0, temp)
    return nums
```

Sample Input/Output:
`
nums = [1,2,3,4,5,6,7], k = 3
Rotated array = [5,6,7,1,2,3,4]
`

---

## 3. Missing Number in Range

Description:
Given an array containing n distinct numbers taken from 0..n, find the missing number.

```python
def missing_number(nums):
    nums.sort()
    for i in range(len(nums)):
        if nums[i] != i:
            return i
    return len(nums)
```

Sample Input/Output:
`
nums = [3,0,1]
Missing = 2
`

---

## 4. Find All Duplicates

Description:
Given an integer array, return all elements that appear more than once.

```python
def find_duplicates(nums):
    res = []
    for i in range(len(nums)):
        for j in range(i+1, len(nums)):
            if nums[i] == nums[j] and nums[i] not in res:
                res.append(nums[i])
    return res
```

Sample Input/Output:
`
nums = [4,3,2,7,8,2,3,1]
Duplicates = [2,3]
`

---

## 5. Merge Two Sorted Arrays

Description:
You are given two sorted arrays. Merge them into one sorted array.

```python
def merge(nums1, nums2):
    nums1.extend(nums2)
    nums1.sort()
    return nums1
```
Sample Input/Output:
`
nums1 = [1,2,3]
nums2 = [2,5,6]
Merged = [1,2,2,3,5,6]
`
---

## 6. Majority Element (> n/2 times)
```python
def majority_element(nums):
    for num in nums:
        if nums.count(num) > len(nums)//2:
            return num
    return None
```

---

## 7. Max Consecutive Ones (with at most one flip)
```python
def find_max_consecutive_ones(nums):
    max_count = 0
    for i in range(len(nums)):
        zero_flipped = False
        count = 0
        for j in range(i, len(nums)):
            if nums[j] == 1:
                count += 1
            elif not zero_flipped:
                zero_flipped = True
                count += 1
            else:
                break
        max_count = max(max_count, count)
    return max_count
```

---

## 8. Find Peak Element
```python
def find_peak(nums):
    for i in range(1, len(nums)-1):
        if nums[i] > nums[i-1] and nums[i] > nums[i+1]:
            return i
    return 0
```

---

## 9. Trapping Rain Water
```python
def trap(height):
    total = 0
    for i in range(len(height)):
        left = max(height[:i+1])
        right = max(height[i:])
        total += min(left, right) - height[i]
    return total
```

---

## 10. Maximum Product Subarray
```python
def max_product(nums):
    result = 0
    for i in range(len(nums)):
        prod = 1
        for j in range(i, len(nums)):
            prod *= nums[j]
            result = max(result, prod)
    return result
```

---

## 11. 3Sum Problem
```python
def three_sum(nums):
    res = []
    for i in range(len(nums)):
        for j in range(i+1, len(nums)):
            for k in range(j+1, len(nums)):
                if nums[i] + nums[j] + nums[k] == 0:
                    triplet = sorted([nums[i], nums[j], nums[k]])
                    if triplet not in res:
                        res.append(triplet)
    return res
```

---

## 12. Kth Largest Element
```python
def kth_largest(nums, k):
    nums.sort(reverse=True)
    return nums[k-1]
```

---

## 13. Sliding Window Maximum
```python
def max_sliding_window(nums, k):
    res = []
    for i in range(len(nums)-k+1):
        res.append(max(nums[i:i+k]))
    return res
```

---

## 14. Set Matrix Zeroes (2D Array)
```python
def set_zeroes(matrix):
    for i in range(len(matrix)):
        for j in range(len(matrix[0])):
            if matrix[i][j] == 0:
                for k in range(len(matrix)):
                    matrix[k][j] = 0
                for l in range(len(matrix[0])):
                    matrix[i][l] = 0
    return matrix
```

---

## 15. Spiral Order Traversal
```python
def spiral_order(matrix):
    res = []
    while matrix:
        res += matrix.pop(0)
        if matrix and matrix[0]:
            for row in matrix:
                res.append(row.pop())
        if matrix:
            res += matrix.pop()[::-1]
        if matrix and matrix[0]:
            for row in matrix[::-1]:
                res.append(row.pop(0))
    return res
```

---
