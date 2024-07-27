# [110. Balanced Binary Tree](https://leetcode.com/problems/balanced-binary-tree/)

![](https://badgen.net/badge/Level/Easy/green)

Given a binary tree, determine if it is 
height-balanced.

A height-balanced binary tree is a binary tree in which the depth of the two subtrees of every node never differs by more than one.
### Approach Used :

-   The solution determines if a binary tree is height-balanced by recursively calculating the height of each subtree while checking if the difference in heights between the left and right subtrees exceeds 1. If any subtree is found to be unbalanced, it updates a boolean reference to indicate the overall imbalance.

### Code (C++)

```cpp
class Solution {
public:
    bool isBalanced(TreeNode* root) {
        bool isBalancedTree = true;
        getHeightAndCheckBalance(root, isBalancedTree);
        return isBalancedTree;
    }

private:
    // Returns the height of the tree rooted at 'node' and sets 'isBalancedTree' to false if the tree is unbalanced.
    int getHeightAndCheckBalance(TreeNode* node, bool& isBalancedTree) {
        if (node == nullptr || !isBalancedTree)
            return 0;

        int leftHeight = getHeightAndCheckBalance(node->left, isBalancedTree);
        int rightHeight = getHeightAndCheckBalance(node->right, isBalancedTree);

        if (abs(leftHeight - rightHeight) > 1)
            isBalancedTree = false;

        return max(leftHeight, rightHeight) + 1;
    }
};
```

### Time Complexity:
- **O(n):**  because each node is visited exactly once

### Space Complexity:
- **O(h):** due to the recursive call stack. 

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>