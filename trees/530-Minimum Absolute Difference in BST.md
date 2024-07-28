# [530. Minimum Absolute Difference in BST](https://leetcode.com/problems/minimum-absolute-difference-in-bst/)

![](https://badgen.net/badge/Level/Easy/green)

Given the root of a Binary Search Tree (BST), return the minimum absolute difference between the values of any two different nodes in the tree.

### Approach Used :

-  An in-order traversal of a BST yields a sorted sequence of node values. By keeping track of the previous node value during the traversal, we can compute the differences between consecutive node values and find the minimum difference.

### Code (C++)

```cpp
class Solution {
public:
    int getMinimumDifference(TreeNode* root) {
        int minDiff = INT_MAX;
        TreeNode* prev = nullptr;
        inOrder(root, prev, minDiff);
        return minDiff;
    }
    
private:
    void inOrder(TreeNode* node, TreeNode*& prev, int& minDiff) {
        if (!node) return;
        
        inOrder(node->left, prev, minDiff);
    
        if (prev != nullptr) {
            minDiff = min(minDiff, node->val - prev->val);
        }
        prev = node;
        
        inOrder(node->right, prev, minDiff);
    }
};
```

### Time Complexity:
- **O(n):** This is because we visit each node exactly once during the in-order traversal.

### Space Complexity:
- **O(h):** due to recursion stack.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>