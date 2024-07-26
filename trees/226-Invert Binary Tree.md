# [226. Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree/)

![](https://badgen.net/badge/Level/Easy/green)

Given the root of a binary tree, invert the tree, and return its root.

### Approach Used :

-   The approach recursively inverts the binary tree by first swapping the left and right children of the current node and then applying the same process to each subtree.

### Code (C++)

```cpp
class Solution {
public:
    TreeNode* invertTree(TreeNode* root) {
        if(!root)
            return root;
        
        //swap
        TreeNode* temp = root->left;
        root->left = root->right;
        root->right = temp;

        //invert
        invertTree(root->left);
        invertTree(root->right);

        return root;
    }
};
```

### Time Complexity:
- **O(n):** because each node is visited once.

### Space Complexity:
- **O(h):** where h is the height of the tree, due to recursion stack.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>