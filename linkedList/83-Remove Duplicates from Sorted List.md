# [83. Remove Duplicates from Sorted List](https://leetcode.com/problems/remove-duplicates-from-sorted-list/)

![](https://badgen.net/badge/Level/Easy/green)

Given the head of a sorted linked list, delete all duplicates such that each element appears only once. Return the linked list sorted as well.

### Approach Used :

-   The approach iterates through the linked list, comparing each node with its next node. If duplicate nodes are found, the next node is deleted and the current node's next pointer is updated; otherwise, it moves to the next node.

### Code (C++)

```cpp
class Solution {
public:
    ListNode* deleteDuplicates(ListNode* head) {
        if(!head || head->next == NULL)
            return head;

        ListNode* curr = head;

        while(curr != NULL && curr->next != NULL){
            if(curr->val == curr->next->val){
                //delete next node
                ListNode* del = curr->next;
                curr->next = del->next;
                delete del;
            }else{
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
- **O(1):** no extra space is used.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>