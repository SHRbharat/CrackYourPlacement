# [Predecessor and Successor](https://www.geeksforgeeks.org/problems/predecessor-and-successor/1)

![](https://badgen.net/badge/Level/Medium/yellow)

There is BST given with the root node with the key part as an integer only. You need to find the in-order successor and predecessor of a given key. If either predecessor or successor is not found, then set it to NULL.

Note:- In an inorder traversal the number just smaller than the target is the predecessor and the number just greater than the target is the successor. 

### Approach Used :

-   To find the in-order predecessor and successor of a given key in a Binary Search Tree (BST), we can leverage the BST properties. The in-order predecessor is the largest node in the left subtree (just smaller than the given key), and the in-order successor is the smallest node in the right subtree (just greater than the given key).

-   Predecessor:
    -   Traverse the tree. If the current node's key is less than the given key, it could be a potential predecessor, so move to the right subtree to find a closer one.
    -   If the key is found and it has a left child, the predecessor is the maximum value node in its left subtree.
-   Successor:
    -   If the current node's key is greater than the given key, it could be a potential successor, so move to the left subtree to find a closer one.
    -   If the key is found and it has a right child, the successor is the minimum value node in its right subtree.

### Code (C++)

```cpp
class Solution
{
    public:
    void findPreSuc(Node* root, Node*& pre, Node*& suc, int key)
    {
        pre = suc = NULL;

        // Traverse the BST to find the key
        while (root != nullptr) {
            if (root->key < key) {
                pre = root; // Possible predecessor
                root = root->right;
            }
            else if (root->key > key) {
                suc = root; // Possible successor
                root = root->left;
            }
            else {
                // If the node with key is found, handle left and right children.
                
                // Find predecessor: largest in the left subtree
                if (root->left != nullptr) {
                    Node* temp = root->left;
                    while (temp->right) {
                        temp = temp->right;
                    }
                    pre = temp;
                }
                
                // Find successor: smallest in the right subtree
                if (root->right != nullptr) {
                    Node* temp = root->right;
                    while (temp->left) {
                        temp = temp->left;
                    }
                    suc = temp;
                }
                return; // Exit since we've handled the key node
            }
        }
    }
};

```

### Time Complexity:
- **O(h):**  where h is the height of the BST. In the worst case, it could be O(n) for a skewed tree, but in a balanced BST, it is O(log n).

### Space Complexity:
- **O(1):** no extra space is used.

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>