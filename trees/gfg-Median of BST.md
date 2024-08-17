# [Median of BST](https://www.geeksforgeeks.org/problems/median-of-bst/1)

![](https://badgen.net/badge/Level/Easy/green)

Given a Binary Search Tree of size N, find the Median of its Node values.

### Approach Used :

-   inorder traversal gives nodes in sorted order.

### Code (C++)

```cpp
void inorder(vector<int>& arr, Node *root) {
    if (!root) return;
    
    inorder(arr, root->left);
    arr.push_back(root->data); 
    inorder(arr, root->right);
}

// Function to find the median of the BST
float findMedian(Node *root) {
    vector<int> nodes;
    inorder(nodes, root);
    
    int n = nodes.size();
    if (n == 0) return 0; // Edge case: Empty tree, though typically it should not happen
    
    if (n % 2 == 0) {
        // Even number of elements, median is the average of the middle two elements
        return (nodes[n / 2 - 1] + nodes[n / 2]) / 2.0;
    } else {
        // Odd number of elements, median is the middle element
        return nodes[n / 2];
    }
}
```

### Time Complexity:
- **O():** since each node is visited once.

### Space Complexity:
- **O(n):** for storing nodes.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>