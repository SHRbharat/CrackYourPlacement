# [Rearrange a given linked list in-place.](https://www.geeksforgeeks.org/rearrange-a-given-linked-list-in-place/)

![](https://badgen.net/badge/Level/Medium/yellow)

Given a singly linked list L0 -> L1 -> … -> Ln-1 -> Ln. Rearrange the nodes in the list so that the new formed list is : L0 -> Ln -> L1 -> Ln-1 -> L2 -> Ln-2 … You are required to do this in place without altering the nodes’ values

### Approach Used :

-   Find the middle point using tortoise and hare method.
-   Split the linked list into two halves using found middle point in step 1.
-   Reverse the second half.
-   Do alternate merge of first and second halves.

### Code (C++)

```cpp
struct Node {
    int data;
    struct Node* next;
};
 
// Function to create newNode in a linkedlist
Node* newNode(int key)
{
    Node* temp = new Node;
    temp->data = key;
    temp->next = NULL;
    return temp;
}
 
// Function to reverse the linked list
void reverselist(Node** head)
{
    // Initialize prev and current pointers
    Node *prev = NULL, *curr = *head, *next;
 
    while (curr) {
        next = curr->next;
        curr->next = prev;
        prev = curr;
        curr = next;
    }
    *head = prev;
}

void rearrange(Node** head)
{
    // 1) Find the middle point using tortoise and hare
    // method
    Node *slow = *head, *fast = slow->next;
    while (fast && fast->next) {
        slow = slow->next;
        fast = fast->next->next;
    }
    // 2) Split the linked list in two halves
    // head1, head of first half    1 -> 2
    // head2, head of second half   3 -> 4
    Node* head1 = *head;
    Node* head2 = slow->next;
    slow->next = NULL;
    // 3) Reverse the second half, i.e.,  4 -> 3
    reverselist(&head2);
    // 4) Merge alternate nodes
    *head = newNode(0); // Assign dummy Node
    // curr is the pointer to this dummy Node, which will
    // be used to form the new list
    Node* curr = *head;
    while (head1 || head2) {
        // First add the element from list
        if (head1) {
            curr->next = head1;
            curr = curr->next;
            head1 = head1->next;
        }
        // Then add the element from the second list
        if (head2) {
            curr->next = head2;
            curr = curr->next;
            head2 = head2->next;
        }
    }
    // Assign the head of the new list to head pointer
    *head = (*head)->next;
}
```

### Time Complexity:
- **O(n):** traversed once.

### Space Complexity:
- **O(1):** no extra space is used.

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>