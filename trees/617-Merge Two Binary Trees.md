# [617. Merge Two Binary Trees](https://leetcode.com/problems/merge-two-binary-trees/)

![](https://badgen.net/badge/Level/Easy/green)

You are given two binary trees root1 and root2.

Imagine that when you put one of them to cover the other, some nodes of the two trees are overlapped while the others are not. You need to merge the two trees into a new binary tree. The merge rule is that if two nodes overlap, then sum node values up as the new value of the merged node. Otherwise, the NOT null node will be used as the node of the new tree.

Return the merged tree.

### Approach Used :

-   The approach recursively merges two binary trees by creating a new tree where each node's value is the sum of the corresponding nodes' values from the two input trees. If a node exists in only one tree, that node's value is used directly in the new tree, and this process is applied to both the left and right children recursively.

### Code (C++)

```cpp
class Solution {
public:
    TreeNode* mergeTrees(TreeNode* root1, TreeNode* root2) {
        if (!root1) return root2;
        if (!root2) return root1;

        TreeNode* mergedRoot = new TreeNode(root1->val + root2->val);
        mergedRoot->left = mergeTrees(root1->left, root2->left);
        mergedRoot->right = mergeTrees(root1->right, root2->right);
        return mergedRoot;
    }
};
```

### Time Complexity:
- **O(n):**  where n is the total number of nodes in the larger of the two trees

### Space Complexity:
- **O(h):** where h is the height of the deeper tree, due to the recursion stack.

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>