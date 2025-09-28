## 1. [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)

```python
class Solution:
    def isValid(self, s: str) -> bool:
        stack, mapping = [], {')':'(', ']':'[', '}':'{'}
        for ch in s:
            if ch in mapping:
                if not stack or stack[-1] != mapping[ch]:
                    return False
                stack.pop()
            else:
                stack.append(ch)
        return not stack
```

---

## 2. [Min Stack](https://leetcode.com/problems/min-stack/)

```python
class MinStack:
    def __init__(self):
        self.stack, self.min_stack = [], []

    def push(self, val: int) -> None:
        self.stack.append(val)
        if not self.min_stack or val <= self.min_stack[-1]:
            self.min_stack.append(val)

    def pop(self) -> None:
        if self.stack.pop() == self.min_stack[-1]:
            self.min_stack.pop()

    def top(self) -> int:
        return self.stack[-1]

    def getMin(self) -> int:
        return self.min_stack[-1]
```

---

## 3. [Implement Stack using Queues](https://leetcode.com/problems/implement-stack-using-queues/)

```python
from collections import deque

class MyStack:
    def __init__(self):
        self.q = deque()

    def push(self, x: int) -> None:
        self.q.append(x)
        for _ in range(len(self.q) - 1):
            self.q.append(self.q.popleft())

    def pop(self) -> int:
        return self.q.popleft()

    def top(self) -> int:
        return self.q[0]

    def empty(self) -> bool:
        return not self.q
```

---

## 4. [Remove Outermost Parentheses](https://leetcode.com/problems/remove-outermost-parentheses/)

```python
class Solution:
    def removeOuterParentheses(self, s: str) -> str:
        res, opened = [], 0
        for ch in s:
            if ch == '(' and opened > 0:
                res.append(ch)
            if ch == ')' and opened > 1:
                res.append(ch)
            opened += 1 if ch == '(' else -1
        return "".join(res)
```

---

## 5. [Baseball Game](https://leetcode.com/problems/baseball-game/)

```python
class Solution:
    def calPoints(self, ops):
        stack = []
        for op in ops:
            if op == "C":
                stack.pop()
            elif op == "D":
                stack.append(2 * stack[-1])
            elif op == "+":
                stack.append(stack[-1] + stack[-2])
            else:
                stack.append(int(op))
        return sum(stack)
```

---

## 6. [Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/)

```python
class Solution:
    def nextGreaterElement(self, nums1, nums2):
        stack, mapping = [], {}
        for num in nums2:
            while stack and num > stack[-1]:
                mapping[stack.pop()] = num
            stack.append(num)
        return [mapping.get(num, -1) for num in nums1]
```

---

## 7. [Next Greater Element II](https://leetcode.com/problems/next-greater-element-ii/)

```python
class Solution:
    def nextGreaterElements(self, nums):
        n, res, stack = len(nums), [-1] * len(nums), []
        for i in range(2 * n):
            while stack and nums[stack[-1]] < nums[i % n]:
                res[stack.pop()] = nums[i % n]
            if i < n:
                stack.append(i)
        return res
```

---

## 8. [Daily Temperatures](https://leetcode.com/problems/daily-temperatures/)

```python
class Solution:
    def dailyTemperatures(self, T):
        res, stack = [0] * len(T), []
        for i, t in enumerate(T):
            while stack and T[stack[-1]] < t:
                idx = stack.pop()
                res[idx] = i - idx
            stack.append(i)
        return res
```

---

## 9. [Simplify Path](https://leetcode.com/problems/simplify-path/)

```python
class Solution:
    def simplifyPath(self, path: str) -> str:
        stack = []
        for part in path.split("/"):
            if part == "..":
                if stack: stack.pop()
            elif part and part != ".":
                stack.append(part)
        return "/" + "/".join(stack)
```

---

## 10. [Backspace String Compare](https://leetcode.com/problems/backspace-string-compare/)

```python
class Solution:
    def backspaceCompare(self, s: str, t: str) -> bool:
        def build(string):
            stack = []
            for ch in string:
                if ch != "#":
                    stack.append(ch)
                elif stack:
                    stack.pop()
            return "".join(stack)
        return build(s) == build(t)
```

---

## 11. [Asteroid Collision](https://leetcode.com/problems/asteroid-collision/)

```python
class Solution:
    def asteroidCollision(self, asteroids):
        stack = []
        for a in asteroids:
            while stack and a < 0 < stack[-1]:
                if stack[-1] < -a:
                    stack.pop()
                    continue
                elif stack[-1] == -a:
                    stack.pop()
                break
            else:
                stack.append(a)
        return stack
```

---

## 12. [Evaluate Reverse Polish Notation](https://leetcode.com/problems/evaluate-reverse-polish-notation/)

```python
class Solution:
    def evalRPN(self, tokens):
        stack = []
        for token in tokens:
            if token in "+-*/":
                b, a = stack.pop(), stack.pop()
                if token == "+":
                    stack.append(a + b)
                elif token == "-":
                    stack.append(a - b)
                elif token == "*":
                    stack.append(a * b)
                else:
                    stack.append(int(a / b))
            else:
                stack.append(int(token))
        return stack[0]
```

---

## 13. [Longest Valid Parentheses](https://leetcode.com/problems/longest-valid-parentheses/)

```python
class Solution:
    def longestValidParentheses(self, s: str) -> int:
        stack, res, start = [], 0, -1
        for i, ch in enumerate(s):
            if ch == '(':
                stack.append(i)
            else:
                if not stack:
                    start = i
                else:
                    stack.pop()
                    if not stack:
                        res = max(res, i - start)
                    else:
                        res = max(res, i - stack[-1])
        return res
```

---

## 14. [Online Stock Span](https://leetcode.com/problems/online-stock-span/)

```python
class StockSpanner:
    def __init__(self):
        self.stack = []

    def next(self, price: int) -> int:
        span = 1
        while self.stack and self.stack[-1][0] <= price:
            span += self.stack.pop()[1]
        self.stack.append((price, span))
        return span
```

---

## 15. [Car Fleet](https://leetcode.com/problems/car-fleet/)

```python
class Solution:
    def carFleet(self, target: int, position, speed):
        cars = sorted(zip(position, speed), reverse=True)
        stack = []
        for pos, spd in cars:
            time = (target - pos) / spd
            if not stack or time > stack[-1]:
                stack.append(time)
        return len(stack)
```

---
