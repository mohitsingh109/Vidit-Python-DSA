# Tree Data Structure

---

## 1. Introduction to Trees

A **Tree** is a hierarchical data structure consisting of nodes.  
- Each node contains a **value** and **links to child nodes**.  
- The **root** is the top-most node.  
- **Leaf nodes** have no children.  
- A **binary tree** is a tree where each node has at most two children (`left`, `right`).

### Why Trees?
- Natural representation of hierarchical data (filesystems, org charts, XML/JSON).
- Widely used in databases, compilers, networking, AI, and search problems.

---

## 2. Common Operations on Trees

| Operation                          | Average Time | Worst Case | Space Complexity |
|------------------------------------|--------------|------------|------------------|
| Insert a node (BST)                | O(log n)     | O(n)       | O(1)             |
| Search for a node (BST)            | O(log n)     | O(n)       | O(1)             |
| Delete a node (BST)                | O(log n)     | O(n)       | O(1)             |
| Traversals (DFS: inorder, preorder, postorder) | O(n) | O(n) | O(h) recursion stack |
| Traversal (BFS: level order)       | O(n)         | O(n)       | O(n)             |
| Height of a tree                   | O(n)         | O(n)       | O(h)             |
| Check balance (AVL/Red-Black Trees)| O(log n)     | O(log n)   | O(1)             |

---

## 3. LeetCode Practice Problems (Trees)

(Easy → Medium) to strengthen your tree skills:

1. [Maximum Depth of Binary Tree (#104)](https://leetcode.com/problems/maximum-depth-of-binary-tree/)  
2. [Minimum Depth of Binary Tree (#111)](https://leetcode.com/problems/minimum-depth-of-binary-tree/)  
3. [Same Tree (#100)](https://leetcode.com/problems/same-tree/)  
4. [Symmetric Tree (#101)](https://leetcode.com/problems/symmetric-tree/)  
5. [Invert Binary Tree (#226)](https://leetcode.com/problems/invert-binary-tree/)  
6. [Binary Tree Level Order Traversal (#102)](https://leetcode.com/problems/binary-tree-level-order-traversal/)  
7. [Binary Tree Zigzag Level Order Traversal (#103)](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/)  
8. [Binary Tree Right Side View (#199)](https://leetcode.com/problems/binary-tree-right-side-view/)  
9. [Binary Tree Left Side View (variant)](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/)  
10. [Average of Levels in Binary Tree (#637)](https://leetcode.com/problems/average-of-levels-in-binary-tree/)  
11. [Diameter of Binary Tree (#543)](https://leetcode.com/problems/diameter-of-binary-tree/)  
12. [Path Sum (#112)](https://leetcode.com/problems/path-sum/)  
13. [Path Sum II (#113)](https://leetcode.com/problems/path-sum-ii/)  
14. [Balanced Binary Tree (#110)](https://leetcode.com/problems/balanced-binary-tree/)  
15. [Subtree of Another Tree (#572)](https://leetcode.com/problems/subtree-of-another-tree/)  
16. [Lowest Common Ancestor of a BST (#235)](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/)  
17. [Lowest Common Ancestor of a Binary Tree (#236)](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/)  
18. [Construct Binary Tree from Preorder and Inorder Traversal (#105)](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/)  
19. [Serialize and Deserialize Binary Tree (#297)](https://leetcode.com/problems/serialize-and-deserialize-binary-tree/)  
20. [Populating Next Right Pointers in Each Node (#116)](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/)  

---

## 4. Design-Oriented Tree Problems


1. [Serialize and Deserialize Binary Tree (#297)](https://leetcode.com/problems/serialize-and-deserialize-binary-tree/)  
   - Implement encoding/decoding of binary tree.  

2. [Serialize and Deserialize BST (#449)](https://leetcode.com/problems/serialize-and-deserialize-bst/)  
   - Optimized version for BST.  

3. [Insert into a Binary Search Tree (#701)](https://leetcode.com/problems/insert-into-a-binary-search-tree/)  
   - Design insert logic.  

4. [Delete Node in a BST (#450)](https://leetcode.com/problems/delete-node-in-a-bst/)  
   - Implement BST delete operation.  

5. [Construct Quad Tree (#427)](https://leetcode.com/problems/construct-quad-tree/)  
   - Divide-and-conquer design with quad tree.  

6. [N-ary Tree Preorder Traversal (#589)](https://leetcode.com/problems/n-ary-tree-preorder-traversal/)  
   - General tree traversal.  

7. [N-ary Tree Level Order Traversal (#429)](https://leetcode.com/problems/n-ary-tree-level-order-traversal/)  
   - BFS for N-ary tree.  

8. [Design File System (#1166)](https://leetcode.com/problems/design-file-system/)  
   - Use a tree to implement hierarchical file system.  

9. [Design Search Autocomplete System (#642)](https://leetcode.com/problems/design-search-autocomplete-system/)  
   - Use **Trie (Prefix Tree)** for efficient search.  

10. [Implement Trie (Prefix Tree) (#208)](https://leetcode.com/problems/implement-trie-prefix-tree/)  
    - Design Trie with insert, search, and startsWith.  

---
