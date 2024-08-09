# [Binary Tree to DLL](https://www.geeksforgeeks.org/problems/binary-tree-to-dll/1)

![](https://badgen.net/badge/Level/Hard/red)

Given a Binary Tree (BT), convert it to a Doubly Linked List (DLL) in place. The left and right pointers in nodes will be used as previous and next pointers respectively in converted DLL. The order of nodes in DLL must be the same as the order of the given Binary Tree. The first node of Inorder traversal (leftmost node in BT) must be the head node of the DLL.

Note: h is the tree's height, and this space is used implicitly for the recursion stack.

### Approach Used :

-   To convert a Binary Tree (BT) into a Doubly Linked List (DLL) in place, we can perform an in-order traversal of the tree. During the traversal, we adjust the left and right pointers to function as the previous and next pointers in the DLL.

### Code (C++)

```cpp
class Solution {
public:
    Node* prev = nullptr;  // This will keep track of the previous node in the DLL

    void convertToDLL(Node* root, Node*& head) {
        // Base case
        if (root == nullptr) return;

        // Recur for the left subtree
        convertToDLL(root->left, head);

        // Process the current node
        if (prev == nullptr) {
            // If prev is null, this is the leftmost node, set it as the head of DLL
            head = root;
        } else {
            // Link the previous node with the current node
            root->left = prev;
            prev->right = root;
        }

        // Update prev to the current node
        prev = root;

        // Recur for the right subtree
        convertToDLL(root->right, head);
    }

    Node* bToDLL(Node* root) {
        Node* head = nullptr;
        convertToDLL(root, head);
        return head;
    }
};

```

### Time Complexity:
- **O(n):** The algorithm traverses each node exactly once.

### Space Complexity:
- **O(1):** The space complexity is determined by the height of the tree h due to the recursion stack.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>