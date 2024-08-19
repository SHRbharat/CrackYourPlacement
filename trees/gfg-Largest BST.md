# [Largest BST](https://www.geeksforgeeks.org/problems/largest-bst/1)

![](https://badgen.net/badge/Level/Medium/yellow)

Given a binary tree. Find the size of its largest subtree which is a Binary Search Tree.
Note: Here Size equals the number of nodes in the subtree.

### Approach Used :

-   To find the size of the largest subtree in a binary tree that is also a Binary Search Tree (BST), we can use a bottom-up approach. We will traverse the tree and, for each node, determine whether the subtree rooted at that node is a BST and, if so, calculate the size of that BST.

-   Traverse the tree in a post-order fashion (left, right, root):
    -   For each node, check if the left and right subtrees are BSTs.
    -   Determine the minimum and maximum values in the left and right subtrees.
    -   If the current node's value is greater than the maximum value in the left subtree and less than the minimum value in the right subtree, then the subtree rooted at this node is a BST.
    -   Calculate the size of this BST and update the result.
-   Maintain information at each node:
    -   Size of the subtree.
    -   Whether the subtree is a BST.
    -   Minimum and maximum values in the subtree.

### Code (C++)

```cpp
class Solution {
public:
    struct Info {
        int size;   // Size of the subtree
        int max;    // Maximum value in the subtree
        int min;    // Minimum value in the subtree
        int largestBSTSize;  // Size of the largest BST which is subtree of the current node
        bool isBST; // Is the current subtree a BST?
    };

    Info largestBSTUtil(Node* root) {
        // Base case: An empty tree is a BST of size 0
        if (!root) {
            return {0, INT_MIN, INT_MAX, 0, true};
        }

        // Recursively get info from left and right subtrees
        Info left = largestBSTUtil(root->left);
        Info right = largestBSTUtil(root->right);

        Info current;
        current.size = 1 + left.size + right.size;

        // Check if the current subtree is a BST
        if (left.isBST && right.isBST && root->data > left.max && root->data < right.min) {
            current.min = min(left.min, root->data);
            current.max = max(right.max, root->data);

            current.isBST = true;
            current.largestBSTSize = current.size;
        } else {
            current.isBST = false;
            current.largestBSTSize = max(left.largestBSTSize, right.largestBSTSize);
        }

        return current;
    }

    // Return the size of the largest sub-tree which is also a BST
    int largestBst(Node *root) {
        return largestBSTUtil(root).largestBSTSize;
    }
};
```

### Time Complexity:
- **O(n):** The function visits each node exactly once.

### Space Complexity:
- **O(h):** where h is the height of the tree, due to the recursion stack.

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>