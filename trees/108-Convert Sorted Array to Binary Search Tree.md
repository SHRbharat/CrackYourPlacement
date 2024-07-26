# [108. Convert Sorted Array to Binary Search Tree](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/)

![](https://badgen.net/badge/Level/Easy/green)

Given an integer array nums where the elements are sorted in ascending order, convert it to a 
height-balanced bst.

### Approach Used :

-   The approach uses a divide-and-conquer strategy  by recursively selecting the middle element of the current subarray as the root node and constructing the left and right subtrees from the left and right halves of the subarray, respectively.

### Code (C++)

```cpp
class Solution {
public:
    TreeNode* sortedArrayToBST(vector<int>& nums) {
        return createTree(nums, 0, nums.size() - 1);
    }

private:
    TreeNode* createTree(const vector<int>& nums, int low, int high) {
        if (low > high) {
            return nullptr;
        }
        
        int mid = low + (high - low) / 2;
        TreeNode* node = new TreeNode(nums[mid]);
        node->left = createTree(nums, low, mid - 1);
        node->right = createTree(nums, mid + 1, high);
        
        return node;
    }
};
```

### Time Complexity:
- **O(n):** as each array element is processed once.

### Space Complexity:
- **O(logn):** recursion stack , where logn is the height of tree.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>