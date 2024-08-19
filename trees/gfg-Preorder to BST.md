# [Preorder to BST](https://www.geeksforgeeks.org/problems/preorder-to-postorder4423/1)

![](https://badgen.net/badge/Level/Medium/yellow)

Given an array arr[] of N nodes representing preorder traversal of some BST. You have to build the BST  from the given preorder traversal. 

In Pre-Order traversal, the root node is visited before the left child and right child nodes.

### Approach Used :

-   To construct a Binary Search Tree (BST) from a given preorder traversal, we can use the property that in a preorder traversal, the first element is always the root. The next elements are part of the left subtree until we encounter an element greater than the root, which marks the beginning of the right subtree.

-   Start with the first element as the root: The first element in the preorder array is the root of the BST.
-   Use recursion to build the tree:
    -   Recursively divide the array into left and right subtrees by finding the first element greater than the current root.
    -   The elements before this element form the left subtree, and the elements after form the right subtree.

### Code (C++)

```cpp
typedef struct Node
{
    int data;
    struct Node *left, *right;
} Node;


// A utility function to create a new tree node
Node* newNode( int data )
{
    Node* temp = (Node *)malloc( sizeof( Node ) );
    temp->data = data;
    temp->left = temp->right = NULL;
    return temp;
}

*/

class Solution {
public:
    // Helper function to construct BST from preorder traversal
    Node* buildBST(int pre[], int& index, int key, int min, int max, int size) {
        // Base condition
        if (index >= size) {
            return nullptr;
        }

        Node* root = nullptr;

        // If current key is in range, it becomes the root
        if (key > min && key < max) {
            root = newNode(key);
            index++;

            if (index < size) {
                // Elements in the left subtree should be smaller than key
                root->left = buildBST(pre, index, pre[index], min, key, size);
            }
            if (index < size) {
                // Elements in the right subtree should be greater than key
                root->right = buildBST(pre, index, pre[index], key, max, size);
            }
        }

        return root;
    }

    // Main function to be called to construct BST from preorder traversal
    Node* Bst(int pre[], int size) {
        int index = 0;
        return buildBST(pre, index, pre[0], INT_MIN, INT_MAX, size);
    }
};
```

### Time Complexity:
- **O(n):** Time Complexity: O(n) where n is the number of nodes. 

### Space Complexity:
- **O(n):** for recursion stack.

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>