# [543. Diameter of Binary Tree](https://leetcode.com/problems/diameter-of-binary-tree/)

![](https://badgen.net/badge/Level/Easy/green)

Given the root of a binary tree, return the length of the diameter of the tree.

The diameter of a binary tree is the length of the longest path between any two nodes in a tree. This path may or may not pass through the root.

The length of a path between two nodes is represented by the number of edges between them.

### Approach Used :

-   The approach involves a recursive function to compute the height of each subtree while simultaneously updating the maximum diameter found, which is the sum of the heights of the left and right subtrees at each node. This ensures that we find the longest path between any two nodes in the tree by considering each possible path.

### Code (C++)

```cpp
class Solution {
public:
    int diameterOfBinaryTree(TreeNode* root) {
        int diameter = 0;
        height(root, diameter);
        return diameter;
    }
    
private:
    int height(TreeNode* node, int& diameter) {
        if (!node) return 0;
        
        int leftHeight = height(node->left, diameter);
        int rightHeight = height(node->right, diameter);
        
        diameter = max(diameter, leftHeight + rightHeight);
        
        return max(leftHeight, rightHeight) + 1;
    }
};
```

### Time Complexity:
- **O(n):** This is because we visit each node exactly once during the traversal.

### Space Complexity:
- **O(h):** This space is used by the recursion stack


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>