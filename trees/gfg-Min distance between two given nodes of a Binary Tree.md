# [Min distance between two given nodes of a Binary Tree](https://www.geeksforgeeks.org/problems/min-distance-between-two-given-nodes-of-a-binary-tree/1)

![](https://badgen.net/badge/Level/Medium/yellow)

Given a binary tree with n nodes and two node values, a and b, your task is to find the minimum distance between them. The given two nodes are guaranteed to be in the binary tree and all node values are unique.

### Approach Used :

-   Find the Lowest Common Ancestor (LCA): The LCA of nodes a and b is the deepest node in the tree that is an ancestor of both a and b. The minimum distance between a and b can be derived by calculating the distance from the LCA to both nodes and summing these distances.
-   Calculate the Distance from the LCA to Each Node: Once the LCA is found, the distance from the LCA to a and from the LCA to b is computed. The sum of these two distances gives the minimum distance between a and b.

### Code (C++)

```cpp
class Solution {
public:
    // Function to find the Lowest Common Ancestor (LCA) of nodes a and b
    Node* findLCA(Node* root, int a, int b) {
        if (!root) return nullptr;
        if (root->data == a || root->data == b) return root;
        
        Node* leftLCA = findLCA(root->left, a, b);
        Node* rightLCA = findLCA(root->right, a, b);
        
        if (leftLCA && rightLCA) return root;
        
        return leftLCA != nullptr ? leftLCA : rightLCA;
    }
    
    // Helper function to calculate the distance from the root to a given node
    int findDistance(Node* root, int val, int distance) {
        if (!root) return -1;
        if (root->data == val) return distance;
        
        int leftDistance = findDistance(root->left, val, distance + 1);
        if (leftDistance != -1) return leftDistance;
        
        return findDistance(root->right, val, distance + 1);
    }
    
    // Function to find the minimum distance between nodes a and b
    int findDist(Node* root, int a, int b) {
        Node* lca = findLCA(root, a, b);
        
        int distA = findDistance(lca, a, 0);
        int distB = findDistance(lca, b, 0);
        
        return distA + distB;
    }
};
```

### Time Complexity:
- **O(n):** because each of the above steps is performed sequentially and their time complexities add up.

### Space Complexity:
- **O(h):** for recursion stack.

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>