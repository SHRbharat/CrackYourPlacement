# [Count BST nodes that lie in a given range](https://www.geeksforgeeks.org/problems/count-bst-nodes-that-lie-in-a-given-range/1)

![](https://badgen.net/badge/Level/Easy/green)

Given a Binary Search Tree (BST) and a range l-h(inclusive), count the number of nodes in the BST that lie in the given range.

### Approach Used :

-   The solution uses a recursive helper function to traverse the BST and count number of nodes that fall within the specified range [low, high]. By leveraging the properties of the BST, it selectively traverses the left subtree if the current node's value is greater than low and the right subtree if the current node's value is less than high, thus avoiding unnecessary nodes.

### Code (C++)

```cpp
class Solution{
public:
    int getCount(Node *root, int l, int h)
    {
      // your code goes here
      if(!root){
          return 0;
      }
      int count = 0;
      traverse(root,l,h,count);
      return count;
    }
    
    void traverse(Node* root,int& l,int& h,int& count){
        if(!root) return;
        
        if(root->data > l) traverse(root->left,l,h,count);
        if(root->data >= l && root->data <= h) count++;
        if(root->data < h) traverse(root->right,l,h,count);
    }
};
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