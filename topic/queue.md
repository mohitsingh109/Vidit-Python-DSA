# Queue in Python

## 1. Introduction to Queue
A **queue** is a linear data structure that follows the **FIFO (First In, First Out)** principle.  
- Think of it like a **line at a ticket counter**: the first person to get in line is the first one served.  
- In Python, queues can be implemented using:
  - **collections.deque** (double-ended queue, most efficient)
  - **queue.Queue** (thread-safe, for multithreading)
  - **list** (but inefficient for popping from front)

---

## 2. Common Operations on Queue

| Operation        | Python Code (with deque)       | Average Time | Worst Case |
|------------------|--------------------------------|--------------|------------|
| Enqueue (insert) | `q.append(x)`                  | O(1)         | O(1)       |
| Dequeue (remove) | `q.popleft()`                  | O(1)         | O(1)       |
| Peek (front)     | `q[0]`                         | O(1)         | O(1)       |
| isEmpty          | `len(q) == 0`                  | O(1)         | O(1)       |
| Size             | `len(q)`                       | O(1)         | O(1)       |

---

## 3. LeetCode Practice Problems (Queue)

(Easy → Medium) to strengthen queue skills:

1. [Implement Queue using Stacks](https://leetcode.com/problems/implement-queue-using-stacks/)  
2. [Design Circular Queue](https://leetcode.com/problems/design-circular-queue/)  
3. [Number of Recent Calls](https://leetcode.com/problems/number-of-recent-calls/)  
4. [Moving Average from Data Stream](https://leetcode.com/problems/moving-average-from-data-stream/)  
5. [Dota2 Senate](https://leetcode.com/problems/dota2-senate/)  
6. [Time Needed to Buy Tickets](https://leetcode.com/problems/time-needed-to-buy-tickets/)  
7. [Maximum Depth of Binary Tree (Level Order Traversal)](https://leetcode.com/problems/maximum-depth-of-binary-tree/)  
8. [Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/)  
9. [Binary Tree Zigzag Level Order Traversal](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/)  
10. [Rotting Oranges](https://leetcode.com/problems/rotting-oranges/)  
11. [Shortest Path in Binary Matrix](https://leetcode.com/problems/shortest-path-in-binary-matrix/)  
12. [Open the Lock](https://leetcode.com/problems/open-the-lock/)  
13. [Perfect Squares](https://leetcode.com/problems/perfect-squares/)  
14. [Minimum Knight Moves](https://leetcode.com/problems/minimum-knight-moves/)  
15. [Course Schedule II (Topological Sort)](https://leetcode.com/problems/course-schedule-ii/)  

---

## 4. Design-Oriented Queue Problems

1. **Implement Queue using Stacks** – [LeetCode #232](https://leetcode.com/problems/implement-queue-using-stacks/)  
   - Design a queue with two stacks.  

2. **Design Circular Queue** – [LeetCode #622](https://leetcode.com/problems/design-circular-queue/)  
   - Fixed size queue, supports enqueue/dequeue in O(1).  

3. **Design Circular Deque** – [LeetCode #641](https://leetcode.com/problems/design-circular-deque/)  
   - More flexible: push/pop from both ends.  

4. **Design Hit Counter** – Implement a hit counter that records and returns hits received in the past 5 minutes.  

5. **Design Task Scheduler** – Queue-based scheduling of tasks with cooldown times.  

6. **Design Bounded Blocking Queue** – A multithreaded blocking queue (producer-consumer problem).  

7. **Design Snake Game** – [LeetCode #353](https://leetcode.com/problems/design-snake-game/)  
   - Simulation using queue for snake body.  

8. **Sliding Window Maximum** – [LeetCode #239](https://leetcode.com/problems/sliding-window-maximum/)  
   - Monotonic deque to track max in sliding windows.  

---