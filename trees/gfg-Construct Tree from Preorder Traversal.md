# [Construct Tree from Preorder Traversal](https://www.geeksforgeeks.org/problems/construct-tree-from-preorder-traversal/1)

![](https://badgen.net/badge/Level/Medium/yellow)

Construct a binary tree of size N using two given arrays pre[] and preLN[]. Array pre[] represents preorder traversal of a binary tree. Array preLN[] has only two possible values L and N. The value L in preLN[] indicates that the corresponding node in Binary Tree is a leaf node and value N indicates that the corresponding node is a non-leaf node.
Note: Every node in the binary tree has either 0 or 2 children.

### Approach Used :

-   Recursive Construction:
    -   Start with the first element in the pre[] array as the root.
    -   If the corresponding entry in preLN[] is 'L', the node is a leaf node, so return the node.
    -   If the corresponding entry in preLN[] is 'N', the node is a non-leaf node, so recursively construct the left and right children.
-   Base Case:
    -   The recursion stops when all nodes have been processed (i.e., when the index reaches n).

### Code (C++)

```cpp
// Helper function to construct the binary tree
Node* constructTreeUtil(int& index, int n, int pre[], char preLN[]) {
    // Base case: If all nodes are processed
    if (index >= n) {
        return NULL;
    }

    // Create a new node with the current value in pre[]
    Node* node = new Node(pre[index]);

    // If this node is a leaf, return it
    if (preLN[index] == 'L') {
        index++;
        return node;
    }

    // If this node is not a leaf, construct its left and right children
    index++;
    node->left = constructTreeUtil(index, n, pre, preLN);
    node->right = constructTreeUtil(index, n, pre, preLN);

    return node;
}

// Main function to construct the binary tree
Node* constructTree(int n, int pre[], char preLN[]) {
    int index = 0;
    return constructTreeUtil(index, n, pre, preLN);
}
```

### Time Complexity:
- **O(n):** Each node is processed exactly once.

### Space Complexity:
- **O(h):** due to the recursion stack.

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>