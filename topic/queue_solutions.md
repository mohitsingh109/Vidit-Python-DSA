## 1. [Implement Queue using Stacks](https://leetcode.com/problems/implement-queue-using-stacks/)

```python
class MyQueue:
    def __init__(self):
        self.in_stack, self.out_stack = [], []

    def push(self, x):
        self.in_stack.append(x)

    def pop(self):
        self.peek()
        return self.out_stack.pop()

    def peek(self):
        if not self.out_stack:
            while self.in_stack:
                self.out_stack.append(self.in_stack.pop())
        return self.out_stack[-1]

    def empty(self):
        return not self.in_stack and not self.out_stack
```

---

## 2. [Design Circular Queue](https://leetcode.com/problems/design-circular-queue/)

```python
class MyCircularQueue:
    def __init__(self, k: int):
        self.q = [0] * k
        self.head = self.count = 0
        self.capacity = k

    def enQueue(self, value: int) -> bool:
        if self.isFull(): return False
        tail = (self.head + self.count) % self.capacity
        self.q[tail] = value
        self.count += 1
        return True

    def deQueue(self) -> bool:
        if self.isEmpty(): return False
        self.head = (self.head + 1) % self.capacity
        self.count -= 1
        return True

    def Front(self) -> int:
        return -1 if self.isEmpty() else self.q[self.head]

    def Rear(self) -> int:
        return -1 if self.isEmpty() else self.q[(self.head + self.count - 1) % self.capacity]

    def isEmpty(self) -> bool:
        return self.count == 0

    def isFull(self) -> bool:
        return self.count == self.capacity
```

---

## 3. [Number of Recent Calls](https://leetcode.com/problems/number-of-recent-calls/)

```python
from collections import deque

class RecentCounter:
    def __init__(self):
        self.q = deque()

    def ping(self, t: int) -> int:
        self.q.append(t)
        while self.q[0] < t - 3000:
            self.q.popleft()
        return len(self.q)
```

---

## 4. [Moving Average from Data Stream](https://leetcode.com/problems/moving-average-from-data-stream/)

```python
from collections import deque

class MovingAverage:
    def __init__(self, size: int):
        self.q = deque()
        self.size = size
        self.sum = 0

    def next(self, val: int) -> float:
        self.q.append(val)
        self.sum += val
        if len(self.q) > self.size:
            self.sum -= self.q.popleft()
        return self.sum / len(self.q)
```

---

## 5. [Dota2 Senate](https://leetcode.com/problems/dota2-senate/)

```python
from collections import deque

class Solution:
    def predictPartyVictory(self, senate: str) -> str:
        n = len(senate)
        r, d = deque(), deque()
        for i, c in enumerate(senate):
            if c == "R":
                r.append(i)
            else:
                d.append(i)
        while r and d:
            if r[0] < d[0]:
                r.append(r[0] + n)
            else:
                d.append(d[0] + n)
            r.popleft()
            d.popleft()
        return "Radiant" if r else "Dire"
```

---

## 6. [Time Needed to Buy Tickets](https://leetcode.com/problems/time-needed-to-buy-tickets/)

```python
class Solution:
    def timeRequiredToBuy(self, tickets, k):
        time = 0
        for i, t in enumerate(tickets):
            if i <= k:
                time += min(t, tickets[k])
            else:
                time += min(t, tickets[k] - 1)
        return time
```

---

## 7. [Maximum Depth of Binary Tree (Level Order Traversal)](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

```python
from collections import deque

class Solution:
    def maxDepth(self, root):
        if not root: return 0
        q = deque([root])
        depth = 0
        while q:
            for _ in range(len(q)):
                node = q.popleft()
                if node.left: q.append(node.left)
                if node.right: q.append(node.right)
            depth += 1
        return depth
```

---

## 8. [Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/)

```python
from collections import deque

class Solution:
    def levelOrder(self, root):
        if not root: return []
        q, res = deque([root]), []
        while q:
            level = []
            for _ in range(len(q)):
                node = q.popleft()
                level.append(node.val)
                if node.left: q.append(node.left)
                if node.right: q.append(node.right)
            res.append(level)
        return res
```

---

## 9. [Binary Tree Zigzag Level Order Traversal](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/)

```python
from collections import deque

class Solution:
    def zigzagLevelOrder(self, root):
        if not root: return []
        q, res, left = deque([root]), [], True
        while q:
            level = []
            for _ in range(len(q)):
                node = q.popleft()
                level.append(node.val)
                if node.left: q.append(node.left)
                if node.right: q.append(node.right)
            res.append(level if left else level[::-1])
            left = not left
        return res
```

---

## 10. [Rotting Oranges](https://leetcode.com/problems/rotting-oranges/)

```python
from collections import deque

class Solution:
    def orangesRotting(self, grid):
        rows, cols = len(grid), len(grid[0])
        q, fresh = deque(), 0
        for r in range(rows):
            for c in range(cols):
                if grid[r][c] == 2:
                    q.append((r, c, 0))
                elif grid[r][c] == 1:
                    fresh += 1
        minutes = 0
        while q:
            r, c, minutes = q.popleft()
            for dr, dc in [(1,0),(-1,0),(0,1),(0,-1)]:
                nr, nc = r+dr, c+dc
                if 0 <= nr < rows and 0 <= nc < cols and grid[nr][nc] == 1:
                    grid[nr][nc] = 2
                    fresh -= 1
                    q.append((nr,nc,minutes+1))
        return minutes if fresh == 0 else -1
```

---

## 11. [Shortest Path in Binary Matrix](https://leetcode.com/problems/shortest-path-in-binary-matrix/)

```python
from collections import deque

class Solution:
    def shortestPathBinaryMatrix(self, grid):
        n = len(grid)
        if grid[0][0] or grid[n-1][n-1]: return -1
        q = deque([(0,0,1)])
        visited = {(0,0)}
        while q:
            r,c,d = q.popleft()
            if (r,c) == (n-1,n-1): return d
            for dr,dc in [(1,0),(-1,0),(0,1),(0,-1),(1,1),(-1,-1),(1,-1),(-1,1)]:
                nr,nc = r+dr,c+dc
                if 0 <= nr < n and 0 <= nc < n and not grid[nr][nc] and (nr,nc) not in visited:
                    visited.add((nr,nc))
                    q.append((nr,nc,d+1))
        return -1
```

---

## 12. [Open the Lock](https://leetcode.com/problems/open-the-lock/)

```python
from collections import deque

class Solution:
    def openLock(self, deadends, target):
        dead = set(deadends)
        if "0000" in dead: return -1
        q, visited = deque([("0000",0)]), {"0000"}
        while q:
            comb, steps = q.popleft()
            if comb == target: return steps
            for i in range(4):
                digit = int(comb[i])
                for move in (-1,1):
                    nd = (digit+move) % 10
                    nxt = comb[:i]+str(nd)+comb[i+1:]
                    if nxt not in dead and nxt not in visited:
                        visited.add(nxt)
                        q.append((nxt,steps+1))
        return -1
```

---

## 13. [Perfect Squares](https://leetcode.com/problems/perfect-squares/)

```python
from collections import deque

class Solution:
    def numSquares(self, n):
        squares = [i*i for i in range(1,int(n**0.5)+1)]
        q, visited = deque([(n,0)]), {n}
        while q:
            rem, steps = q.popleft()
            if rem == 0: return steps
            for s in squares:
                nxt = rem - s
                if nxt < 0: break
                if nxt not in visited:
                    visited.add(nxt)
                    q.append((nxt, steps+1))
        return -1
```

---

## 14. [Minimum Knight Moves](https://leetcode.com/problems/minimum-knight-moves/)

```python
from collections import deque

class Solution:
    def minKnightMoves(self, x: int, y: int) -> int:
        x, y = abs(x), abs(y)
        directions = [(1,2),(2,1),(-1,2),(-2,1),(1,-2),(2,-1),(-1,-2),(-2,-1)]
        q, visited = deque([(0,0,0)]), {(0,0)}
        while q:
            cx, cy, steps = q.popleft()
            if (cx,cy) == (x,y): return steps
            for dx,dy in directions:
                nx,ny = cx+dx,cy+dy
                if -2 <= nx <= x+2 and -2 <= ny <= y+2 and (nx,ny) not in visited:
                    visited.add((nx,ny))
                    q.append((nx,ny,steps+1))
```

---

## 15. [Course Schedule II (Topological Sort)](https://leetcode.com/problems/course-schedule-ii/)

```python
from collections import deque

class Solution:
    def findOrder(self, numCourses, prerequisites):
        graph = [[] for _ in range(numCourses)]
        indegree = [0] * numCourses
        for a,b in prerequisites:
            graph[b].append(a)
            indegree[a] += 1
        q = deque([i for i in range(numCourses) if indegree[i] == 0])
        res = []
        while q:
            node = q.popleft()
            res.append(node)
            for nei in graph[node]:
                indegree[nei] -= 1
                if indegree[nei] == 0:
                    q.append(nei)
        return res if len(res) == numCourses else []
```

---

# 🚀 Design-Oriented Queue Problems

- **Implement Queue using Stacks** – [LeetCode #232](https://leetcode.com/problems/implement-queue-using-stacks/)  
- **Design Circular Queue** – [LeetCode #622](https://leetcode.com/problems/design-circular-queue/)  
- **Design Circular Deque** – [LeetCode #641](https://leetcode.com/problems/design-circular-deque/)  
- **Design Hit Counter** – Track hits in past 5 minutes  
- **Design Task Scheduler** – Queue-based scheduling of tasks with cooldowns  
- **Design Bounded Blocking Queue** – Producer-Consumer queue  
- **Design Snake Game** – [LeetCode #353](https://leetcode.com/problems/design-snake-game/)  
- **Sliding Window Maximum** – [LeetCode #239](https://leetcode.com/problems/sliding-window-maximum/)  
- **Design Front Middle Back Queue** – [LeetCode #1670](https://leetcode.com/problems/design-front-middle-back-queue/)  
