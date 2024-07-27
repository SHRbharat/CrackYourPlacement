# [112. Path Sum](https://leetcode.com/problems/path-sum/)

![](https://badgen.net/badge/Level/Easy/green)

Given the root of a binary tree and an integer targetSum, return true if the tree has a root-to-leaf path such that adding up all the values along the path equals targetSum.

### Approach Used :

-   The solution checks if there is a root-to-leaf path in the binary tree such that the sum of the node values along the path equals the target sum. It does this by recursively subtracting the current node's value from the target sum and checking if either the left or right subtree contains such a path, stopping and returning true if a leaf node with the required sum is found.

### Code (C++)

```cpp
class Solution {
public:
    bool hasPathSum(TreeNode* root, int targetSum) {
        if (!root) return false;  
        
        // If the current node is a leaf and its value equals the target sum, return true.
        if (!root->left && !root->right && root->val == targetSum) {
            return true;
        }

        // Subtract the current node's value from the target sum and check both subtrees.
        int newTargetSum = targetSum - root->val;
        return hasPathSum(root->left, newTargetSum) || hasPathSum(root->right, newTargetSum);
    }
};
```

### Time Complexity:
- **O(n):** because each node is visited exactly once.

### Space Complexity:
- **O(h):**  due to the recursive call stack. 

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>