# [101. Symmetric Tree](https://leetcode.com/problems/symmetric-tree/)

![](https://badgen.net/badge/Level/Easy/green)

Given the root of a binary tree, check whether it is a mirror of itself (i.e., symmetric around its center).

### Approach Used-1 (bfs , queue) :

-   The approach uses a BFS to traverse the tree,  comparing nodes at each level for symmetry. By checking pairs of nodes (left and right children) iteratively, it ensures the tree is symmetric by validating that the left subtree is a mirror reflection of the right subtree.

### Code-1(C++)

```cpp
class Solution {
public:
    bool isSymmetric(TreeNode* root) {
        if (!root)
            return true;

        queue<TreeNode*> q;
        q.push(root->left);
        q.push(root->right);

        while (!q.empty()) {
            TreeNode* left = q.front();
            q.pop();
            TreeNode* right = q.front();
            q.pop();

            if (!left && !right)
                continue;
            if (!left || !right)
                return false;
            if (left->val != right->val)
                return false;

            q.push(left->left);
            q.push(right->right);
            q.push(left->right);
            q.push(right->left);
        }
        return true;
    }
};
```

### Time Complexity:
- **O(n):**  since each node is enqueued and dequeued exactly once.

### Space Complexity:
- **O(n):** as the queue may hold up to n nodes in the worst case.

### Approach Used-2 (recursive) :

-   The recursive approach checks if the tree is symmetric by comparing the left and right subtrees of the root node. The helper function isMirror recursively ensures that the left subtree is a mirror reflection of the right subtree by comparing corresponding nodes.

### Code-2(C++)

```cpp
class Solution {
public:
    bool isSymmetric(TreeNode* root) {
        if (!root)
            return true;
        return isMirror(root->left, root->right);
    }

private:
    bool isMirror(TreeNode* left, TreeNode* right) {
        if (!left && !right)
            return true;
        if (!left || !right)
            return false;
        if (left->val != right->val)
            return false;
        return isMirror(left->left, right->right) && isMirror(left->right, right->left);
    }
};
```

### Time Complexity:
- **O(n):**  as each node is visited once.

### Space Complexity:
- **O(h):** where h is the height of the tree, due to the recursive call stack.

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>