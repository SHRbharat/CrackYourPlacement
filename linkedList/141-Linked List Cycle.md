# [141. Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/)

![](https://badgen.net/badge/Level/Easy/green)

Given head, the head of a linked list, determine if the linked list has a cycle in it.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the next pointer. Internally, pos is used to denote the index of the node that tail's next pointer is connected to. Note that pos is not passed as a parameter.

Return true if there is a cycle in the linked list. Otherwise, return false.

### Approach Used :

-   The solution detects a cycle in a linked list using the "two-pointer" technique, where slow moves one step at a time and fast moves two steps at a time. If there is a cycle, fast and slow will eventually meet; if there is no cycle, fast will reach the end of the list.

### Code (C++)

```cpp
class Solution {
public:
    bool hasCycle(ListNode *head) {
        ListNode* slow = head;
        ListNode* fast = head;

        while(fast != NULL && fast->next != NULL){
            fast = fast->next->next;
            slow = slow->next;

            if(fast == slow){
                return true;
            }
        }

        return false;
    }
};
```

### Time Complexity:
- **O(n):** whole list is traversed.

### Space Complexity:
- **O(1):** no extra space is used.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>