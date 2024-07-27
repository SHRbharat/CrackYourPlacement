# [94. Binary Tree Inorder Traversal](https://leetcode.com/problems/binary-tree-inorder-traversal/)

![](https://badgen.net/badge/Level/Easy/green)

Given the root of a binary tree, return the inorder traversal of its nodes' values.

### Approach Used :

-   The solution performs an in-order traversal of the binary tree using a recursive helper function. The helper function visits the left subtree, adds the current node's value to the result vector, and then visits the right subtree, ensuring nodes are processed in the correct in-order sequence.

### Code (C++)

```cpp
class Solution {
public:
    vector<int> inorderTraversal(TreeNode* root) {
        vector<int> res;
        inorder(root,res);
        return res;
    }

    void inorder(TreeNode* node,vector<int>& res){
        if(!node)
            return;
        
        inorder(node->left,res);
        res.push_back(node->val);
        inorder(node->right,res);
    }
};
```

### Time Complexity:
- **O(n):**  because each node is visited exactly once.

### Space Complexity:
- **O(1):** which includes the space required for the result vector and the recursive call stack.

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>