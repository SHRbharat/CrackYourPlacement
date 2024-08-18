# [Rearrange a Linked List in Zig-Zag fashion](https://www.geeksforgeeks.org/linked-list-in-zig-zag-fashion/)

![](https://badgen.net/badge/Level/Medium/yellow)

Given a linked list, rearrange it such that the converted list should be of the form a < b > c < d > e < f … where a, b, c… are consecutive data nodes of the linked list.

### Approach Used :

-   using a single scan similar to bubble sort and then maintain a flag for representing which order () currently we are. If the current two elements are not in that order then swap those elements otherwise not.
    -   Flag-Based Approach: We use a flag (bool flag) to decide whether the current pair of nodes should be in increasing (<) or decreasing (>) order.
        -   If flag is true, we expect the current node's value to be less than the next node's value (< relationship).
        -   If flag is false, we expect the current node's value to be greater than the next node's value (> relationship).
-   Swapping Nodes: As we traverse the linked list:
    -   If the current pair doesn't satisfy the expected relationship, we swap the values of the current node and the next node to enforce the zigzag pattern.
-   Flip the Flag: After checking each pair, the flag is flipped to check for the opposite relationship in the next iteration.

### Code (C++)

```cpp
// This function distributes the Node in zigzag fashion 
void zigZagList(Node* head) 
{ 
    // If flag is true, then next node should be greater in 
    // the desired output. 
    bool flag = true; 
  
    // Traverse linked list starting from head. 
    Node* current = head; 
    while (current->next != NULL) { 
        if (flag) /* "<" relation expected */
        { 
            // If we have a situation like A > B > C where 
            // A, B and C are consecutive Nodes in list we 
            // get A > B < C by swapping B and C 
            if (current->data > current->next->data) 
                swap(current->data, current->next->data); 
        } 
        else /* ">" relation expected */
        { 
            // If we have a situation like A < B < C where 
            // A, B and C  are consecutive Nodes in list we 
            // get A < C > B by swapping B and C 
            if (current->data < current->next->data) 
                swap(current->data, current->next->data); 
        } 
  
        current = current->next; 
        flag = !flag; /* flip flag for reverse checking */
    } 
} 
  
/* UTILITY FUNCTIONS */
/* Function to push a Node */
void push(Node** head_ref, int new_data) 
{ 
    /* allocate Node */
    struct Node* new_Node = new Node; 
  
    /* put in the data  */
    new_Node->data = new_data; 
  
    /* link the old list of the new Node */
    new_Node->next = (*head_ref); 
  
    /* move the head to point to the new Node */
    (*head_ref) = new_Node; 
} 
```

### Time Complexity:
- **O(n):**  We traverse the list once.

### Space Complexity:
- **O(1):** no extra space is used.

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>