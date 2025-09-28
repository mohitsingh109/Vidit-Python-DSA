
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

## 2. Best Time to Buy and Sell Stock
[Problem Link](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

```python
# Import not needed
def maxProfit(prices):
    min_price, max_profit = float('inf'), 0
    for price in prices:
        min_price = min(min_price, price)
        max_profit = max(max_profit, price - min_price)
    return max_profit
```

---

## 3. Contains Duplicate
[Problem Link](https://leetcode.com/problems/contains-duplicate/)

```python
# Import not needed, just set()
def containsDuplicate(nums):
    return len(nums) != len(set(nums))
```

---

## 4. Product of Array Except Self
[Problem Link](https://leetcode.com/problems/product-of-array-except-self/)

```python
# Import not needed
def productExceptSelf(nums):
    n = len(nums)
    res = [1] * n
    prefix = 1
    for i in range(n):
        res[i] = prefix
        prefix *= nums[i]
    suffix = 1
    for i in range(n-1, -1, -1):
        res[i] *= suffix
        suffix *= nums[i]
    return res
```

---

## 5. Maximum Subarray
[Problem Link](https://leetcode.com/problems/maximum-subarray/)

```python
# Import not needed (Kadane’s algorithm)
def maxSubArray(nums):
    cur_sum = max_sum = nums[0]
    for num in nums[1:]:
        cur_sum = max(num, cur_sum + num)
        max_sum = max(max_sum, cur_sum)
    return max_sum
```

---

## 6. Merge Sorted Array
[Problem Link](https://leetcode.com/problems/merge-sorted-array/)

```python
# Import not needed
def merge(nums1, m, nums2, n):
    while m > 0 and n > 0:
        if nums1[m-1] > nums2[n-1]:
            nums1[m+n-1] = nums1[m-1]
            m -= 1
        else:
            nums1[m+n-1] = nums2[n-1]
            n -= 1
    nums1[:n] = nums2[:n]
```

---

## 7. Majority Element
[Problem Link](https://leetcode.com/problems/majority-element/)

```python
# Import collections for Counter
from collections import Counter

def majorityElement(nums):
    count = Counter(nums)
    return max(count, key=count.get)
```

---

## 8. Rotate Array
[Problem Link](https://leetcode.com/problems/rotate-array/)

```python
# Import not needed
def rotate(nums, k):
    k %= len(nums)
    nums[:] = nums[-k:] + nums[:-k]
```

---

## 9. Intersection of Two Arrays II
[Problem Link](https://leetcode.com/problems/intersection-of-two-arrays-ii/)

```python
# Import Counter
from collections import Counter

def intersect(nums1, nums2):
    c1, c2 = Counter(nums1), Counter(nums2)
    res = []
    for num in c1:
        res.extend([num] * min(c1[num], c2[num]))
    return res
```

---

## 10. Move Zeroes
[Problem Link](https://leetcode.com/problems/move-zeroes/)

```python
# Import not needed
def moveZeroes(nums):
    j = 0
    for i in range(len(nums)):
        if nums[i] != 0:
            nums[i], nums[j] = nums[j], nums[i]
            j += 1
```

---

## 11. Find All Numbers Disappeared in an Array
[Problem Link](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/)

```python
# Import not needed
def findDisappearedNumbers(nums):
    for num in nums:
        idx = abs(num) - 1
        if nums[idx] > 0:
            nums[idx] *= -1
    return [i+1 for i, num in enumerate(nums) if num > 0]
```

---

## 12. Third Maximum Number
[Problem Link](https://leetcode.com/problems/third-maximum-number/)

```python
# Import not needed
def thirdMax(nums):
    nums = set(nums)
    if len(nums) < 3:
        return max(nums)
    nums.remove(max(nums))
    nums.remove(max(nums))
    return max(nums)
```

---

## 13. Reshape the Matrix
[Problem Link](https://leetcode.com/problems/reshape-the-matrix/)

```python
# Import not needed
def matrixReshape(mat, r, c):
    flat = [num for row in mat for num in row]
    if len(flat) != r * c:
        return mat
    return [flat[i*c:(i+1)*c] for i in range(r)]
```

---

## 14. Search in Rotated Sorted Array
[Problem Link](https://leetcode.com/problems/search-in-rotated-sorted-array/)

```python
# Import not needed
def search(nums, target):
    l, r = 0, len(nums) - 1
    while l <= r:
        mid = (l + r) // 2
        if nums[mid] == target:
            return mid
        if nums[l] <= nums[mid]:
            if nums[l] <= target < nums[mid]:
                r = mid - 1
            else:
                l = mid + 1
        else:
            if nums[mid] < target <= nums[r]:
                l = mid + 1
            else:
                r = mid - 1
    return -1
```

---

## 15. Container With Most Water
[Problem Link](https://leetcode.com/problems/container-with-most-water/)

```python
# Import not needed
def maxArea(height):
    l, r = 0, len(height)-1
    max_area = 0
    while l < r:
        max_area = max(max_area, min(height[l], height[r]) * (r-l))
        if height[l] < height[r]:
            l += 1
        else:
            r -= 1
    return max_area
```
