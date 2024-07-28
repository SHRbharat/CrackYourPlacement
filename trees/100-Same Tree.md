# [100. Same Tree](https://leetcode.com/problems/same-tree/)

![](https://badgen.net/badge/Level/Easy/green)

Given the roots of two binary trees p and q, write a function to check if they are the same or not.

Two binary trees are considered the same if they are structurally identical, and the nodes have the same value.

### Approach Used :

-   The approach recursively checks whether two binary trees are identical by comparing the values of corresponding nodes and ensuring both the left and right subtrees are also identical. The base cases handle when both nodes are null (trees are identical) or when only one node is null (trees are not identical), and if the values differ at any node, the trees are also not identical.

### Code (C++)

```cpp
class Solution {
public:
    bool isSameTree(TreeNode* p, TreeNode* q) {
        if (!p && !q) return true;
        if (!p || !q) return false;
        if (p->val != q->val) return false;
        
        return isSameTree(p->left, q->left) && isSameTree(p->right, q->right);
    }
};
```

### Time Complexity:
- **O(n):** because each node is visited exactly once.

### Space Complexity:
- **O(h):** due to the recursion stack.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>