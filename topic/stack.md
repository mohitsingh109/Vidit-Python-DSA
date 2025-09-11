# Stack in Python

## 1. Introduction to Stack
A **stack** is a linear data structure that follows the **LIFO (Last In, First Out)** principle.  
- Think of it like a **stack of plates**: the last plate you put on the top is the first one you take off.  
- In Python, a stack can be implemented using:
  - Using Linked List with Node class 
  - **list** with `append()` and `pop()`
  - **collections.deque** (more efficient)
  - **queue.LifoQueue** (thread-safe)

---

## 2. Common Operations on Stack

| Operation       | Python Code (using list) | Average Time | Worst Case |
|-----------------|--------------------------|--------------|------------|
| Push (insert)   | `stack.append(x)`        | O(1)         | O(1)       |
| Pop (remove)    | `stack.pop()`            | O(1)         | O(1)       |
| Peek (top)      | `stack[-1]`              | O(1)         | O(1)       |
| isEmpty         | `len(stack) == 0`        | O(1)         | O(1)       |
| Size            | `len(stack)`             | O(1)         | O(1)       |


---

## 3. LeetCode Practice Problems (Stack)

Here’s a progression of problems (Easy → Medium):

1. [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)  
2. [Min Stack](https://leetcode.com/problems/min-stack/)  
3. [Implement Stack using Queues](https://leetcode.com/problems/implement-stack-using-queues/)  
4. [Remove Outermost Parentheses](https://leetcode.com/problems/remove-outermost-parentheses/)  
5. [Baseball Game](https://leetcode.com/problems/baseball-game/)  
6. [Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/)  
7. [Next Greater Element II](https://leetcode.com/problems/next-greater-element-ii/)  
8. [Daily Temperatures](https://leetcode.com/problems/daily-temperatures/)  
9. [Simplify Path](https://leetcode.com/problems/simplify-path/)  
10. [Backspace String Compare](https://leetcode.com/problems/backspace-string-compare/)  
11. [Asteroid Collision](https://leetcode.com/problems/asteroid-collision/)  
12. [Evaluate Reverse Polish Notation](https://leetcode.com/problems/evaluate-reverse-polish-notation/)  
13. [Longest Valid Parentheses](https://leetcode.com/problems/longest-valid-parentheses/)  
14. [Online Stock Span](https://leetcode.com/problems/online-stock-span/)  
15. [Car Fleet](https://leetcode.com/problems/car-fleet/)  

---

## 4. Design-Oriented Stack Problems

These problems require designing stack-based data structures:

1. **Min Stack** – [LeetCode #155](https://leetcode.com/problems/min-stack/)  
   - Design a stack that supports push, pop, top, and retrieving the minimum element in O(1).  

2. **Implement Stack using Queues** – [LeetCode #225](https://leetcode.com/problems/implement-stack-using-queues/)  
   - Use two queues to simulate stack operations.  

3. **Implement Queue using Stacks** – [LeetCode #232](https://leetcode.com/problems/implement-queue-using-stacks/)  
   - Reverse scenario: implement queue with stacks.  

4. **Design Browser History** – Similar to doubly linked list + stack for back/forward navigation.  

5. **Design Circular Deque** – [LeetCode #641](https://leetcode.com/problems/design-circular-deque/)  
   - Related to stack/queue hybrid design.  

6. **Max Stack (Design Problem)** – Design a stack that supports push, pop, top, and retrieving the maximum element in O(1).  

7. **Decode String** – [LeetCode #394](https://leetcode.com/problems/decode-string/)  
   - Use stack to decode nested encoded strings like `3[a2[c]] → accaccacc`.  

8. **Design a Stack with Increment Operation** – [LeetCode #1381](https://leetcode.com/problems/design-a-stack-with-increment-operation/)  
   - Add an extra operation that increments bottom k elements by val.  

---