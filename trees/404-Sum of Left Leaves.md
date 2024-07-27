# [404. Sum of Left Leaves](https://leetcode.com/problems/sum-of-left-leaves/)

![](https://badgen.net/badge/Level/Easy/green)

Given the root of a binary tree, return the sum of all left leaves.
A leaf is a node with no children. A left leaf is a leaf that is the left child of another node.

### Approach Used :

-   The solution traverses the binary tree recursively, checking if the left child of each node is a leaf (i.e., it has no children). If it is a left leaf, its value is added to the sum, and the function continues to explore both left and right subtrees to sum all left leaves.

### Code (C++)

```cpp
class Solution {
public:
    
    int sumOfLeftLeaves(TreeNode* root) {
        if (!root) return 0;
        int sum = 0;
        if (root->left && !root->left->left && !root->left->right) {
            sum += root->left->val; 
        }
        sum += sumOfLeftLeaves(root->left); 
        sum += sumOfLeftLeaves(root->right);
        return sum;
    }
};
```

### Time Complexity:
- **O(n):**  because each node is visited exactly once.

### Space Complexity:
- **O(h):**  due to the recursive call stack.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>