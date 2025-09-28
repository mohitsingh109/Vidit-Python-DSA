## 1. [Maximum Depth of Binary Tree (#104)](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

```python
class Solution:
    def maxDepth(self, root):
        if not root: return 0
        return 1 + max(self.maxDepth(root.left), self.maxDepth(root.right))
```

---

## 2. [Minimum Depth of Binary Tree (#111)](https://leetcode.com/problems/minimum-depth-of-binary-tree/)

```python
class Solution:
    def minDepth(self, root):
        if not root: return 0
        if not root.left: return 1 + self.minDepth(root.right)
        if not root.right: return 1 + self.minDepth(root.left)
        return 1 + min(self.minDepth(root.left), self.minDepth(root.right))
```

---

## 3. [Same Tree (#100)](https://leetcode.com/problems/same-tree/)

```python
class Solution:
    def isSameTree(self, p, q):
        if not p and not q: return True
        if not p or not q or p.val != q.val: return False
        return self.isSameTree(p.left, q.left) and self.isSameTree(p.right, q.right)
```

---

## 4. [Symmetric Tree (#101)](https://leetcode.com/problems/symmetric-tree/)

```python
class Solution:
    def isSymmetric(self, root):
        def isMirror(t1, t2):
            if not t1 and not t2: return True
            if not t1 or not t2: return False
            return (t1.val == t2.val and
                    isMirror(t1.left, t2.right) and
                    isMirror(t1.right, t2.left))
        return isMirror(root, root)
```

---

## 5. [Invert Binary Tree (#226)](https://leetcode.com/problems/invert-binary-tree/)

```python
class Solution:
    def invertTree(self, root):
        if not root: return None
        root.left, root.right = self.invertTree(root.right), self.invertTree(root.left)
        return root
```

---

## 6. [Binary Tree Level Order Traversal (#102)](https://leetcode.com/problems/binary-tree-level-order-traversal/)

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

## 7. [Binary Tree Zigzag Level Order Traversal (#103)](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/)

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

## 8. [Binary Tree Right Side View (#199)](https://leetcode.com/problems/binary-tree-right-side-view/)

```python
from collections import deque

class Solution:
    def rightSideView(self, root):
        if not root: return []
        q, res = deque([root]), []
        while q:
            res.append(q[-1].val)
            for _ in range(len(q)):
                node = q.popleft()
                if node.left: q.append(node.left)
                if node.right: q.append(node.right)
        return res
```

---

## 9. [Binary Tree Left Side View (variant)](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/)

```python
from collections import deque

class Solution:
    def leftSideView(self, root):
        if not root: return []
        q, res = deque([root]), []
        while q:
            res.append(q[0].val)
            for _ in range(len(q)):
                node = q.popleft()
                if node.left: q.append(node.left)
                if node.right: q.append(node.right)
        return res
```

---

## 10. [Average of Levels in Binary Tree (#637)](https://leetcode.com/problems/average-of-levels-in-binary-tree/)

```python
from collections import deque

class Solution:
    def averageOfLevels(self, root):
        if not root: return []
        q, res = deque([root]), []
        while q:
            total, count = 0, len(q)
            for _ in range(count):
                node = q.popleft()
                total += node.val
                if node.left: q.append(node.left)
                if node.right: q.append(node.right)
            res.append(total / count)
        return res
```

---

## 11. [Diameter of Binary Tree (#543)](https://leetcode.com/problems/diameter-of-binary-tree/)

```python
class Solution:
    def diameterOfBinaryTree(self, root):
        self.diameter = 0
        def depth(node):
            if not node: return 0
            left, right = depth(node.left), depth(node.right)
            self.diameter = max(self.diameter, left + right)
            return 1 + max(left, right)
        depth(root)
        return self.diameter
```

---

## 12. [Path Sum (#112)](https://leetcode.com/problems/path-sum/)

```python
class Solution:
    def hasPathSum(self, root, targetSum):
        if not root: return False
        if not root.left and not root.right:
            return root.val == targetSum
        return (self.hasPathSum(root.left, targetSum - root.val) or
                self.hasPathSum(root.right, targetSum - root.val))
```

---

## 13. [Path Sum II (#113)](https://leetcode.com/problems/path-sum-ii/)

```python
class Solution:
    def pathSum(self, root, targetSum):
        res = []
        def dfs(node, path, total):
            if not node: return
            if not node.left and not node.right and total + node.val == targetSum:
                res.append(path + [node.val])
                return
            dfs(node.left, path + [node.val], total + node.val)
            dfs(node.right, path + [node.val], total + node.val)
        dfs(root, [], 0)
        return res
```

---

## 14. [Balanced Binary Tree (#110)](https://leetcode.com/problems/balanced-binary-tree/)

```python
class Solution:
    def isBalanced(self, root):
        def check(node):
            if not node: return 0
            left, right = check(node.left), check(node.right)
            if left == -1 or right == -1 or abs(left - right) > 1:
                return -1
            return 1 + max(left, right)
        return check(root) != -1
```

---

## 15. [Subtree of Another Tree (#572)](https://leetcode.com/problems/subtree-of-another-tree/)

```python
class Solution:
    def isSubtree(self, root, subRoot):
        if not root: return False
        if self.isSame(root, subRoot): return True
        return self.isSubtree(root.left, subRoot) or self.isSubtree(root.right, subRoot)
    
    def isSame(self, s, t):
        if not s and not t: return True
        if not s or not t or s.val != t.val: return False
        return self.isSame(s.left, t.left) and self.isSame(s.right, t.right)
```

---

## 16. [Lowest Common Ancestor of a BST (#235)](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/)

```python
class Solution:
    def lowestCommonAncestor(self, root, p, q):
        if p.val < root.val and q.val < root.val:
            return self.lowestCommonAncestor(root.left, p, q)
        elif p.val > root.val and q.val > root.val:
            return self.lowestCommonAncestor(root.right, p, q)
        else:
            return root
```

---

## 17. [Lowest Common Ancestor of a Binary Tree (#236)](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/)

```python
class Solution:
    def lowestCommonAncestor(self, root, p, q):
        if not root or root == p or root == q: return root
        left, right = self.lowestCommonAncestor(root.left, p, q), self.lowestCommonAncestor(root.right, p, q)
        if left and right: return root
        return left if left else right
```

---

## 18. [Construct Binary Tree from Preorder and Inorder Traversal (#105)](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/)

```python
class Solution:
    def buildTree(self, preorder, inorder):
        if not preorder or not inorder: return None
        root_val = preorder.pop(0)
        root = TreeNode(root_val)
        idx = inorder.index(root_val)
        root.left = self.buildTree(preorder, inorder[:idx])
        root.right = self.buildTree(preorder, inorder[idx+1:])
        return root
```

---

## 19. [Serialize and Deserialize Binary Tree (#297)](https://leetcode.com/problems/serialize-and-deserialize-binary-tree/)

```python
from collections import deque

class Codec:
    def serialize(self, root):
        res = []
        def dfs(node):
            if not node:
                res.append("N")
                return
            res.append(str(node.val))
            dfs(node.left)
            dfs(node.right)
        dfs(root)
        return ",".join(res)

    def deserialize(self, data):
        vals = deque(data.split(","))
        def dfs():
            val = vals.popleft()
            if val == "N":
                return None
            node = TreeNode(int(val))
            node.left = dfs()
            node.right = dfs()
            return node
        return dfs()
```

---

## 20. [Populating Next Right Pointers in Each Node (#116)](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/)

```python
from collections import deque

class Solution:
    def connect(self, root):
        if not root: return None
        q = deque([root])
        while q:
            size = len(q)
            for i in range(size):
                node = q.popleft()
                if i < size - 1:
                    node.next = q[0]
                if node.left: q.append(node.left)
                if node.right: q.append(node.right)
        return root
```

---
