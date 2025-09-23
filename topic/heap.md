# Heap in Python

## Introduction to Heap
A **Heap** is a special Tree-based data structure that satisfies the **Heap Property**:  
- In a **Min-Heap**, the parent node is always smaller than or equal to its children.  
- In a **Max-Heap**, the parent node is always larger than or equal to its children.  

Heaps are widely used for **priority queues, scheduling, and streaming problems**.

---

## Common Operations on Heap (Python)
Python provides the **`heapq`** module for heaps. It implements a **Min-Heap** by default.

```python
import heapq

# Create a heap
heap = []
heapq.heappush(heap, 10)
heapq.heappush(heap, 5)
heapq.heappush(heap, 20)

print(heap)  # [5, 10, 20]

# Pop the smallest element
print(heapq.heappop(heap))  # 5

# Peek smallest (without popping)
print(heap[0])  # 10

# Convert list into a heap (in-place)
nums = [3, 1, 4, 2]
heapq.heapify(nums)
print(nums)  # [1, 2, 4, 3]

# Max-Heap (using negative values)
max_heap = []
heapq.heappush(max_heap, -10)
heapq.heappush(max_heap, -5)
print(-heapq.heappop(max_heap))  # 10
```

---

## LeetCode Practice Problems (Heap)

### Easy
1. [Min Cost Climbing Stairs (#746)](https://leetcode.com/problems/min-cost-climbing-stairs/)  
2. [Kth Largest Element in a Stream (#703)](https://leetcode.com/problems/kth-largest-element-in-a-stream/)  
3. [Last Stone Weight (#1046)](https://leetcode.com/problems/last-stone-weight/)  
4. [Relative Ranks (#506)](https://leetcode.com/problems/relative-ranks/)  
5. [Sort Characters By Frequency (#451)](https://leetcode.com/problems/sort-characters-by-frequency/)  

### Medium
6. [Kth Largest Element in an Array (#215)](https://leetcode.com/problems/kth-largest-element-in-an-array/)  
7. [Top K Frequent Elements (#347)](https://leetcode.com/problems/top-k-frequent-elements/)  
8. [Find K Pairs with Smallest Sums (#373)](https://leetcode.com/problems/find-k-pairs-with-smallest-sums/)  
9. [Ugly Number II (#264)](https://leetcode.com/problems/ugly-number-ii/)  
10. [Reorganize String (#767)](https://leetcode.com/problems/reorganize-string/)  
11. [Task Scheduler (#621)](https://leetcode.com/problems/task-scheduler/)  
12. [Meeting Rooms II (#253)](https://leetcode.com/problems/meeting-rooms-ii/)  
13. [IPO (#502)](https://leetcode.com/problems/ipo/)  
14. [Find Median from Data Stream (#295)](https://leetcode.com/problems/find-median-from-data-stream/)  
15. [Sliding Window Median (#480)](https://leetcode.com/problems/sliding-window-median/)  

---

## 🛠️ Design-Oriented Heap Problems
1. [Kth Largest Element in a Stream (#703)](https://leetcode.com/problems/kth-largest-element-in-a-stream/) – **Design a class that maintains the Kth largest element dynamically.**  
2. [Find Median from Data Stream (#295)](https://leetcode.com/problems/find-median-from-data-stream/) – **Design a data structure to return running median.**  
3. [Seat Reservation Manager (#1845)](https://leetcode.com/problems/seat-reservation-manager/) – **Design a manager that reserves/unreserves the smallest available seat.**  
4. [Single-Threaded CPU (#1834)](https://leetcode.com/problems/single-threaded-cpu/) – **Design CPU scheduling system using heaps.**  
5. [Twitter Design (#355)](https://leetcode.com/problems/design-twitter/) – **Use heaps to maintain top tweets by timestamp.**  

---