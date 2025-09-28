## Easy

### 1. Min Cost Climbing Stairs (#746)
[Problem Link](https://leetcode.com/problems/min-cost-climbing-stairs/)

```python
# Import not needed
def minCostClimbingStairs(cost):
    n = len(cost)
    dp = [0] * (n+1)
    for i in range(2, n+1):
        dp[i] = min(dp[i-1] + cost[i-1], dp[i-2] + cost[i-2])
    return dp[n]
```

---

### 2. Kth Largest Element in a Stream (#703)
[Problem Link](https://leetcode.com/problems/kth-largest-element-in-a-stream/)

```python
# Import heapq for min-heap operations
import heapq

class KthLargest:
    def __init__(self, k, nums):
        self.k = k
        self.heap = nums
        heapq.heapify(self.heap)
        while len(self.heap) > k:
            heapq.heappop(self.heap)

    def add(self, val):
        heapq.heappush(self.heap, val)
        if len(self.heap) > self.k:
            heapq.heappop(self.heap)
        return self.heap[0]
```

---

### 3. Last Stone Weight (#1046)
[Problem Link](https://leetcode.com/problems/last-stone-weight/)

```python
# Import heapq, use max heap by negating values
import heapq

def lastStoneWeight(stones):
    stones = [-s for s in stones]
    heapq.heapify(stones)
    while len(stones) > 1:
        x, y = -heapq.heappop(stones), -heapq.heappop(stones)
        if x != y:
            heapq.heappush(stones, -(x-y))
    return -stones[0] if stones else 0
```

---

### 4. Relative Ranks (#506)
[Problem Link](https://leetcode.com/problems/relative-ranks/)

```python
# Import not needed
def findRelativeRanks(score):
    sorted_scores = sorted(score, reverse=True)
    rank_map = {}
    for i, val in enumerate(sorted_scores):
        if i == 0:
            rank_map[val] = "Gold Medal"
        elif i == 1:
            rank_map[val] = "Silver Medal"
        elif i == 2:
            rank_map[val] = "Bronze Medal"
        else:
            rank_map[val] = str(i+1)
    return [rank_map[s] for s in score]
```

---

### 5. Sort Characters By Frequency (#451)
[Problem Link](https://leetcode.com/problems/sort-characters-by-frequency/)

```python
# Import Counter for counting and heapq for sorting by frequency
from collections import Counter
import heapq

def frequencySort(s):
    count = Counter(s)
    heap = [(-freq, char) for char, freq in count.items()]
    heapq.heapify(heap)
    res = []
    while heap:
        freq, char = heapq.heappop(heap)
        res.append(char * -freq)
    return "".join(res)
```

---

## Medium

### 6. Kth Largest Element in an Array (#215)
[Problem Link](https://leetcode.com/problems/kth-largest-element-in-an-array/)

```python
# Import heapq for heap operations
import heapq

def findKthLargest(nums, k):
    return heapq.nlargest(k, nums)[-1]
```

---

### 7. Top K Frequent Elements (#347)
[Problem Link](https://leetcode.com/problems/top-k-frequent-elements/)

```python
# Import Counter and heapq
from collections import Counter
import heapq

def topKFrequent(nums, k):
    count = Counter(nums)
    return [num for num, _ in heapq.nlargest(k, count.items(), key=lambda x: x[1])]
```

---

### 8. Find K Pairs with Smallest Sums (#373)
[Problem Link](https://leetcode.com/problems/find-k-pairs-with-smallest-sums/)

```python
# Import heapq
import heapq

def kSmallestPairs(nums1, nums2, k):
    if not nums1 or not nums2:
        return []
    heap = []
    for i in range(min(k, len(nums1))):
        heapq.heappush(heap, (nums1[i]+nums2[0], i, 0))
    res = []
    while heap and len(res) < k:
        s, i, j = heapq.heappop(heap)
        res.append([nums1[i], nums2[j]])
        if j+1 < len(nums2):
            heapq.heappush(heap, (nums1[i]+nums2[j+1], i, j+1))
    return res
```

---

### 9. Ugly Number II (#264)
[Problem Link](https://leetcode.com/problems/ugly-number-ii/)

```python
# Import not needed (DP with pointers)
def nthUglyNumber(n):
    ugly = [1]
    i2 = i3 = i5 = 0
    for _ in range(1, n):
        next_ugly = min(ugly[i2]*2, ugly[i3]*3, ugly[i5]*5)
        ugly.append(next_ugly)
        if next_ugly == ugly[i2]*2: i2 += 1
        if next_ugly == ugly[i3]*3: i3 += 1
        if next_ugly == ugly[i5]*5: i5 += 1
    return ugly[-1]
```

---

### 10. Reorganize String (#767)
[Problem Link](https://leetcode.com/problems/reorganize-string/)

```python
# Import Counter and heapq
from collections import Counter
import heapq

def reorganizeString(s):
    count = Counter(s)
    heap = [(-freq, char) for char, freq in count.items()]
    heapq.heapify(heap)
    prev = (0, '')
    res = []
    while heap:
        freq, char = heapq.heappop(heap)
        res.append(char)
        if prev[0] < 0:
            heapq.heappush(heap, prev)
        freq += 1
        prev = (freq, char)
    return "".join(res) if len(res) == len(s) else ""
```

---

### 11. Task Scheduler (#621)
[Problem Link](https://leetcode.com/problems/task-scheduler/)

```python
# Import Counter and heapq
from collections import Counter
import heapq

def leastInterval(tasks, n):
    count = Counter(tasks)
    heap = [-c for c in count.values()]
    heapq.heapify(heap)
    time = 0
    while heap:
        temp = []
        for _ in range(n+1):
            if heap:
                val = heapq.heappop(heap)
                if val+1 < 0:
                    temp.append(val+1)
            time += 1
            if not heap and not temp:
                break
        for item in temp:
            heapq.heappush(heap, item)
    return time
```

---

### 12. Meeting Rooms II (#253)
[Problem Link](https://leetcode.com/problems/meeting-rooms-ii/)

```python
# Import heapq
import heapq

def minMeetingRooms(intervals):
    if not intervals:
        return 0
    intervals.sort(key=lambda x: x[0])
    heap = [intervals[0][1]]
    for i in intervals[1:]:
        if i[0] >= heap[0]:
            heapq.heappop(heap)
        heapq.heappush(heap, i[1])
    return len(heap)
```

---

### 13. IPO (#502)
[Problem Link](https://leetcode.com/problems/ipo/)

```python
# Import heapq
import heapq

def findMaximizedCapital(k, w, profits, capital):
    projects = sorted(zip(capital, profits))
    i = 0
    max_heap = []
    for _ in range(k):
        while i < len(projects) and projects[i][0] <= w:
            heapq.heappush(max_heap, -projects[i][1])
            i += 1
        if not max_heap:
            break
        w -= heapq.heappop(max_heap)
    return w
```

---

### 14. Find Median from Data Stream (#295)
[Problem Link](https://leetcode.com/problems/find-median-from-data-stream/)

```python
# Import heapq
import heapq

class MedianFinder:
    def __init__(self):
        self.small, self.large = [], []

    def addNum(self, num):
        heapq.heappush(self.small, -num)
        if self.small and self.large and -self.small[0] > self.large[0]:
            heapq.heappush(self.large, -heapq.heappop(self.small))
        if len(self.small) > len(self.large)+1:
            heapq.heappush(self.large, -heapq.heappop(self.small))
        if len(self.large) > len(self.small):
            heapq.heappush(self.small, -heapq.heappop(self.large))

    def findMedian(self):
        if len(self.small) > len(self.large):
            return -self.small[0]
        return (-self.small[0] + self.large[0]) / 2
```

---

### 15. Sliding Window Median (#480)
[Problem Link](https://leetcode.com/problems/sliding-window-median/)

```python
# Import heapq (requires balancing two heaps with lazy deletion)
import heapq

class DualHeap:
    def __init__(self, k):
        self.small, self.large = [], []
        self.delayed = {}
        self.k = k
        self.small_size = self.large_size = 0

    def prune(self, heap):
        while heap and self.delayed.get(heap[0][1 if heap == self.large else 0], 0):
            num = heap[0][1 if heap == self.large else 0]
            self.delayed[num] -= 1
            if self.delayed[num] == 0:
                del self.delayed[num]
            heapq.heappop(heap)

    def rebalance(self):
        if self.small_size > self.large_size + 1:
            heapq.heappush(self.large, -heapq.heappop(self.small))
            self.small_size -= 1
            self.large_size += 1
            self.prune(self.small)
        elif self.small_size < self.large_size:
            heapq.heappush(self.small, -heapq.heappop(self.large))
            self.small_size += 1
            self.large_size -= 1
            self.prune(self.large)

    def insert(self, num):
        if not self.small or num <= -self.small[0]:
            heapq.heappush(self.small, -num)
            self.small_size += 1
        else:
            heapq.heappush(self.large, num)
            self.large_size += 1
        self.rebalance()

    def erase(self, num):
        self.delayed[num] = self.delayed.get(num, 0) + 1
        if num <= -self.small[0]:
            self.small_size -= 1
            if num == -self.small[0]:
                self.prune(self.small)
        else:
            self.large_size -= 1
            if self.large and num == self.large[0]:
                self.prune(self.large)
        self.rebalance()

    def getMedian(self):
        if self.k % 2:
            return -self.small[0]
        return (-self.small[0] + self.large[0]) / 2

def medianSlidingWindow(nums, k):
    dh = DualHeap(k)
    res = []
    for i, num in enumerate(nums):
        dh.insert(num)
        if i >= k - 1:
            res.append(dh.getMedian())
            dh.erase(nums[i-k+1])
    return res
```

---

## Design-Oriented Heap Problems

### 1. Kth Largest Element in a Stream (#703)
*(Already solved above in Easy)*

### 2. Find Median from Data Stream (#295)
*(Already solved above in Medium)*

### 3. Seat Reservation Manager (#1845)
[Problem Link](https://leetcode.com/problems/seat-reservation-manager/)

```python
# Import heapq for priority queue
import heapq

class SeatManager:
    def __init__(self, n):
        self.available = list(range(1, n+1))
        heapq.heapify(self.available)

    def reserve(self):
        return heapq.heappop(self.available)

    def unreserve(self, seatNumber):
        heapq.heappush(self.available, seatNumber)
```

---

### 4. Single-Threaded CPU (#1834)
[Problem Link](https://leetcode.com/problems/single-threaded-cpu/)

```python
# Import heapq
import heapq

def getOrder(tasks):
    tasks = sorted([(t[0], t[1], i) for i, t in enumerate(tasks)])
    res, heap = [], []
    time, i = 0, 0
    while heap or i < len(tasks):
        if not heap and time < tasks[i][0]:
            time = tasks[i][0]
        while i < len(tasks) and tasks[i][0] <= time:
            heapq.heappush(heap, (tasks[i][1], tasks[i][2]))
            i += 1
        dur, idx = heapq.heappop(heap)
        time += dur
        res.append(idx)
    return res
```

---

### 5. Twitter Design (#355)
[Problem Link](https://leetcode.com/problems/design-twitter/)

```python
# Import defaultdict and heapq
from collections import defaultdict
import heapq

class Twitter:
    def __init__(self):
        self.time = 0
        self.tweets = defaultdict(list)
        self.following = defaultdict(set)

    def postTweet(self, userId, tweetId):
        self.time += 1
        self.tweets[userId].append((self.time, tweetId))

    def getNewsFeed(self, userId):
        heap = []
        self.following[userId].add(userId)
        for followee in self.following[userId]:
            for t in self.tweets[followee][-10:]:
                heapq.heappush(heap, t)
                if len(heap) > 10:
                    heapq.heappop(heap)
        return [tweetId for _, tweetId in sorted(heap, reverse=True)]

    def follow(self, followerId, followeeId):
        self.following[followerId].add(followeeId)

    def unfollow(self, followerId, followeeId):
        if followeeId in self.following[followerId]:
            self.following[followerId].remove(followeeId)
```
