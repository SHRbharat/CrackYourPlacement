# [Flattening a Linked List](https://www.geeksforgeeks.org/problems/flattening-a-linked-list/1)

![](https://badgen.net/badge/Level/Medium/yellow)

Given a Linked List, where every node represents a sub-linked-list and contains two pointers:
(i) a next pointer to the next node,
(ii) a bottom pointer to a linked list where this node is head.
Each of the sub-linked lists is in sorted order.
Flatten the Link List so all the nodes appear in a single level while maintaining the sorted order.

Note: The flattened list will be printed using the bottom pointer instead of the next pointer. Look at the printList() function in the driver code for more clarity.

### Approach Used :

-   Base Case:
    -   If the root is NULL or has no next node, return the root as it is already a single list.
-   Flatten Recursively:
    -   Flatten the list starting from the next node.
    -   Merge the result with the current node’s bottom list.
-   Merge Two Lists:
    -   Merge two sorted linked lists using a similar approach to the merge step in merge sort.

### Code (C++)

```cpp
struct Node{
    int data;
    struct Node * next;
    struct Node * bottom;

    Node(int x){
        data = x;
        next = NULL;
        bottom = NULL;
    }

};

struct Node{
    int data;
    struct Node * next;
    struct Node * bottom;

    Node(int x){
        data = x;
        next = NULL;
        bottom = NULL;
    }

};

class Solution {
public:
    // Function to merge two sorted linked lists
    Node* merge(Node* a, Node* b) {
        // Create a dummy node to simplify merging
        Node* dummy = new Node(0);
        Node* tail = dummy;

        // Merge the lists
        while (a && b) {
            if (a->data < b->data) {
                tail->bottom = a;
                a = a->bottom;
            } else {
                tail->bottom = b;
                b = b->bottom;
            }
            tail = tail->bottom;
        }

        // Append the remaining nodes
        if (a) tail->bottom = a;
        if (b) tail->bottom = b;

        // The merged list starts from dummy->bottom
        return dummy->bottom;
    }

    // Function which returns the root of the flattened linked list
    Node* flatten(Node* root) {
        // Base case
        if (!root || !root->next) return root;

        // Recursively flatten the next list
        root->next = flatten(root->next);

        // Merge the current list with the flattened next list
        root = merge(root, root->next);

        return root;
    }
};

```

### Time Complexity:
- **O(nlogn):** Each node is processed once, and merging is done in linear time.

### Space Complexity:
- **O(1):** no extra space is used.

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>