# [257. Binary Tree Paths](https://leetcode.com/problems/binary-tree-paths/)

![](https://badgen.net/badge/Level/Easy/green)

description-paste here

### Approach Used :

-   The solution uses a Depth-First Search (DFS) approach to traverse the binary tree. It constructs paths from the root to each leaf node by recursively appending the node values to the current path string and storing the complete paths in a vector when a leaf node is reached.

### Code (C++)

```cpp
class Solution {
public:
    vector<string> binaryTreePaths(TreeNode* root) {
        vector<string> paths;
        if (root) {
            string currentPath = to_string(root->val);
            dfs(root, currentPath, paths);
        }
        return paths;
    }
    
private:
    void dfs(TreeNode* node, string currentPath, vector<string>& paths) {
        // Base case: if the node is a leaf, add the path to the result
        if (!node->left && !node->right) {
            paths.push_back(currentPath);
            return;
        }

        // Recurse on the left child if it exists
        if (node->left) {
            dfs(node->left, currentPath + "->" + to_string(node->left->val), paths);
        }
        
        // Recurse on the right child if it exists
        if (node->right) {
            dfs(node->right, currentPath + "->" + to_string(node->right->val), paths);
        }
    }
};
```

### Time Complexity:
- **O(n * h):** This accounts for traversing all nodes and constructing the path strings.

### Space Complexity:
- **O(n * h):** due to the space needed for storing the paths and the recursion stack


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>