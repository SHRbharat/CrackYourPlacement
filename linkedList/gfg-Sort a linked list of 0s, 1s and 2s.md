# [Sort a linked list of 0s, 1s and 2s](https://www.geeksforgeeks.org/sort-a-linked-list-of-0s-1s-or-2s/)

![](https://badgen.net/badge/Level/Easy/green)

Given a linked list of 0s, 1s and 2s, The task is to sort and print it.

### Approach Used-1 (updating values) :

-   The idea is to traverse the Linked List and count the number of nodes having values 0, 1 and 2 and store them in an array of size 3, say cnt[] 

- Now, traverse the linked list again to fill the first cnt[0] nodes with 0, then next cnt[1] nodes with 1 and finally next cnt[2] nodes with 2.


### Code-1 (C++)

```cpp
void sortList(Node* head) {
      
    // Initialize count of '0', '1' and '2' as 0
    int cnt[3] = { 0, 0, 0 };
    Node* ptr = head;

    while (ptr != NULL) {
        cnt[ptr->data] += 1;
        ptr = ptr->next;
    }

    int idx = 0;
    ptr = head;
    
    while (ptr != nullptr) {
          
        if (cnt[idx] == 0)
            idx += 1;
        else {
            ptr->data = idx;
            cnt[idx] -= 1;
            ptr = ptr->next;
        }
    }
}
```

### Time Complexity:
- **O(n):** traverses the list once.

### Space Complexity:
- **O(1):** no extra space is used.

### Approach Used-2 (updating links) :

-   The idea is to maintain 3 pointers named zero, one and two to point to current ending nodes of linked lists containing 0, 1, and 2 respectively. For every traversed node, we attach it to the end of its corresponding list.

- Finally, we link all three lists. To avoid many null checks, we use three dummy pointers zeroD, oneD and twoD that work as dummy headers of three lists.

### Code (C++)

```cpp
Node* sortList(Node* head) {
    if (!head || !(head->next)) 
        return head; 

    // Create three dummy nodes to point to beginning of three linked lists. These dummy nodes are created to avoid null checks. 
    Node* zeroD = new Node(0); 
    Node* oneD = new Node(0); 
    Node* twoD = new Node(0);

    // Initialize current pointers for three lists 
    Node *zero = zeroD, *one = oneD, *two = twoD; 

    // Traverse list 
    Node* curr = head; 
    while (curr) { 
        if (curr->data == 0) { 
            
            zero->next = curr; 
            zero = zero->next; 
        } 
        else if (curr->data == 1) { 
            
            one->next = curr; 
            one = one->next; 
        } 
        else { 
              
            two->next = curr; 
            two = two->next; 
        } 
        curr = curr->next; 
    } 

    // Combine the three lists
    zero->next = (oneD->next) ? (oneD->next) : (twoD->next); 
    one->next = twoD->next; 
    two->next = NULL; 
      
    // Updated head 
    head = zeroD->next; 

    // Delete dummy nodes 
    delete zeroD; 
    delete oneD; 
    delete twoD; 

    return head; 
} 
```

### Time Complexity:
- **O(n):** traverses the list once.

### Space Complexity:
- **O(1):** no extra space is used.
### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>