# [Check whether BST contains Dead End](https://www.geeksforgeeks.org/problems/check-whether-bst-contains-dead-end/1)

![](https://badgen.net/badge/Level/Medium/yellow)

Given a Binary Search Tree that contains unique positive integer values greater than 0. The task is to complete the function isDeadEnd which returns true if the BST contains a dead end else returns false. Here Dead End means a leaf node, at which no other node can be inserted.

### Approach Used :

-   Inorder Traversal:
    -   The inorder function traverses the BST in inorder fashion (left-root-right) and populates two arrays: arr for all nodes and leaf for leaf nodes only.
    -   It also initializes arr with {0} to handle edge cases where the smallest node might be 1.
-   Checking for Dead Ends:
    -   After populating arr and leaf, the function iterates through arr and leaf to check if any leaf node is a dead end.
    -   A leaf node is a dead end if arr[i-1] is equal to leaf[j] - 1 and arr[i+1] is equal to leaf[j] + 1, indicating that the leaf node is surrounded by consecutive integers, making it impossible to insert any other node.

### Code (C++)

```cpp
class Solution{
  public:
    vector<int> arr, leaf;
    
    void inorder(Node* node){
        if(!node)
            return;
        
        inorder(node->left);
        arr.push_back(node->data);
        if(!node->left && !node->right)
            leaf.push_back(node->data);
        inorder(node->right);
    }
    
    bool isDeadEnd(Node *root)
    {
        arr = {0}; 
        leaf = {};
        inorder(root);
        
        int j = 0;
        for(int i = 1; i < arr.size() && j < leaf.size(); ++i){
            if(arr[i] == leaf[j]){
                if(arr[i-1] == leaf[j] - 1 && arr[i+1] == leaf[j] + 1)
                    return true;
                ++j;
            }
        }
        
        return false;
    }
};
```

### Time Complexity:
- **O(n):** inorder traversal.

### Space Complexity:
- **O(n):** to store all nodes in arr and leaf nodes in leaf..

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>