# [104. Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

![](https://badgen.net/badge/Level/Easy/green)

Given the root of a binary tree, return its maximum depth.

A binary tree's maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

### Approach Used :

-   The recursive DFS approach calculates the maximum depth by traversing the tree and computing the depth of the left and right subtrees for each node. The depth of a node is determined as the greater depth of its two subtrees plus one, accounting for the current node itself.

### Code (C++)

```cpp
class Solution {
public:
    int maxDepth(TreeNode* root) {
        if (!root) return 0;
        return dfs(root);
    }

private:
    int dfs(TreeNode* node) {
        if (!node) return 0;
        int leftDepth = dfs(node->left);
        int rightDepth = dfs(node->right);
        return max(leftDepth, rightDepth) + 1;
    }
};

```

### Time Complexity:
- **O(n):** since each node is visited once.

### Space Complexity:
- **O(h):** due to the recursive call stack.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>