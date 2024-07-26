# [203. Remove Linked List Elements](https://leetcode.com/problems/remove-linked-list-elements/)

![](https://badgen.net/badge/Level/Easy/green)

Given the head of a linked list and an integer val, remove all the nodes of the linked list that has Node.val == val, and return the new head.

### Approach Used :

-   The approach iterates through the linked list, first removing all nodes from the head that have the given value val. Once the head is correctly positioned, it iterates through the rest of the list, removing any subsequent nodes with the value val by updating pointers to bypass the deleted nodes. This ensures all nodes with the specified value are removed while maintaining the structure of the list.


### Code (C++)

```cpp
class Solution {
public:
    ListNode* removeElements(ListNode* head, int val) {
        // Handle deletion at the head
        while (head != NULL && head->val == val) {
            ListNode* temp = head;
            head = head->next;
            delete temp;
        }

        // handle the rest of the list
        ListNode* curr = head;
        while (curr != NULL && curr->next != NULL) {
            if (curr->next->val == val) {
                ListNode* temp = curr->next;
                curr->next = curr->next->next;
                delete temp;
            } else {
                curr = curr->next;
            }
        }
        
        return head;
    }
};
```

### Time Complexity:
- **O(n):** traverses the list once.

### Space Complexity:
- **O(1):** no extra space is created.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>