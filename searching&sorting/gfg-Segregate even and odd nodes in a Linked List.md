# [Segregate even and odd nodes in a Linked List](https://www.geeksforgeeks.org/segregate-even-and-odd-elements-in-a-linked-list/)

![](https://badgen.net/badge/Level/Medium/yellow)

Given a Linked List of integers, write a function to modify the linked list such that all even numbers appear before all the odd numbers in the modified linked list. Also, keep the order of even and odd numbers the same.

### Approach Used :

-   The idea is to get a pointer to the last node of list. And then traverse the list starting from the head node and move the odd valued nodes from their current position to end of the list.

    -   Get a pointer to the last node. 
    -   Move all the odd nodes to the end. 
        -   Consider all odd nodes before the first even node and move them to end. 
        -   Change the head pointer to point to the first even node. 
        -   Consider all odd nodes after the first even node and move them to the end. 

### Code (C++)

```cpp
class Node 
{ 
public: 
    int data; 
    Node *next; 
    Node (int d) {
        data = d;
        next = nullptr;
    }
}; 

void segregateEvenOdd(Node **head_ref) 
{ 
    Node *end = *head_ref; 
    Node *prev = nullptr; 
    Node *curr = *head_ref; 

    /* Get pointer to the last node */
    while (end->next != nullptr) 
        end = end->next; 

    Node *new_end = end; 

    /* Consider all odd nodes before the first 
    even node and move then after end */
    while (curr->data % 2 != 0 && curr != end) 
    { 
        new_end->next = curr; 
        curr = curr->next; 
        new_end->next->next = nullptr; 
        new_end = new_end->next; 
    } 

    // 10->8->17->17->15 
    /* Do following steps only if 
    there is any even node */
    if (curr->data%2 == 0) 
    { 
        /* Change the head pointer to 
        point to first even node */
        *head_ref = curr; 

        /* now current points to 
        the first even node */
        while (curr != end) 
        { 
            if ( (curr->data) % 2 == 0 ) 
            { 
                prev = curr; 
                curr = curr->next; 
            } 
            else
            { 
                /* break the link between 
                prev and current */
                prev->next = curr->next; 

                /* Make next of curr as NULL */
                curr->next = nullptr; 

                /* Move curr to end */
                new_end->next = curr; 

                /* make curr as new end of list */
                new_end = curr; 

                /* Update current pointer to 
                next of the moved node */
                curr = prev->next; 
            } 
        } 
    } 

    /* We must have prev set before executing 
    lines following this statement */
    else prev = curr; 

    /* If there are more than 1 odd nodes 
    and end of original list is odd then 
    move this node to end to maintain 
    same order of odd numbers in modified list */
    if (new_end != end && (end->data) % 2 != 0) 
    { 
        prev->next = end->next; 
        end->next = nullptr; 
        new_end->next = end; 
    } 
    return; 
} 

```

### Time Complexity:
- **O(n):** As we are only traversing linearly through the list.

### Space Complexity:
- **O(1):** no extra space is used.

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>