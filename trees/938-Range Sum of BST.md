# [938. Range Sum of BST](https://leetcode.com/problems/range-sum-of-bst/)

![](https://badgen.net/badge/Level/Easy/green)

Given the root node of a binary search tree and two integers low and high, return the sum of values of all nodes with a value in the inclusive range [low, high].

### Approach Used :

-   The solution uses a recursive helper function to traverse the BST and sum the values of nodes that fall within the specified range [low, high]. By leveraging the properties of the BST, it selectively traverses the left subtree if the current node's value is greater than low and the right subtree if the current node's value is less than high, thus avoiding unnecessary nodes.

### Code (C++)

```cpp
class Solution {
public:
    int rangeSumBST(TreeNode* root, int low, int high) {
        if (!root) return 0;
        
        int sum = 0;
        rangeSumBSTHelper(root, low, high, sum);
        return sum;
    }

private:
    void rangeSumBSTHelper(TreeNode* node, int low, int high, int& sum) {
        if (!node) return;

        // If current node's value is greater than low, 
        // then its left child might have nodes within range.
        if (node->val > low) {
            rangeSumBSTHelper(node->left, low, high, sum);
        }

        // If current node's value is within range, 
        // add its value to sum.
        if (node->val >= low && node->val <= high) {
            sum += node->val;
        }

        // If current node's value is less than high, 
        // then its right child might have nodes within range.
        if (node->val < high) {
            rangeSumBSTHelper(node->right, low, high, sum);
        }
    }
};

// class Solution {
// public:
//     int rangeSumBST(TreeNode* root, int low, int high) {
//         if (!root) return 0;

//         int sum = 0;
//         if (root->val >= low && root->val <= high) {
//             sum += root->val;
//         }
//         if (root->val > low) {
//             sum += rangeSumBST(root->left, low, high);
//         }
//         if (root->val < high) {
//             sum += rangeSumBST(root->right, low, high);
//         }
//         return sum;
//     }
// };
```

### Time Complexity:
- **O(n):** whole tree is traversed in worst case.

### Space Complexity:
- **O(h):** due to recusrion stack.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>