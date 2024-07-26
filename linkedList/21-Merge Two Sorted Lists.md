# [21. Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)

![](https://badgen.net/badge/Level/Easy/green)

You are given the heads of two sorted linked lists list1 and list2.

Merge the two lists into one sorted list. The list should be made by splicing together the nodes of the first two lists.

Return the head of the merged linked list.

### Approach Used-1 :

-   Use a dummy node to simplify merging two sorted linked lists by iteratively attaching the smaller node from either list to the merged list.Once one list is exhausted, attach the remaining part of the other list directly to the merged list.

### Code-1 (C++)

```cpp
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
        // Create a dummy node to act as the starting point of the new list
        ListNode dummy;
        ListNode* tail = &dummy;

        // Loop until either list1 or list2 is empty
        while (list1 && list2) {
            if (list1->val < list2->val) {
                tail->next = list1;
                list1 = list1->next;
            } else {
                tail->next = list2;
                list2 = list2->next;
            }
            tail = tail->next;
        }

        // Attach the remaining part of list1 or list2
        if (list1) {
            tail->next = list1;
        } else {
            tail->next = list2;
        }

        // The dummy node's next pointer points to the head of the merged list
        return dummy.next;
    }
};
```

### Time Complexity:
- **O(n+m):** where n and m are the lengths of the two lists.

### Space Complexity:
- **O(1):** no extra space is used.

### Approach Used-2 (recursion):

-   The function recursively compares the heads of the two lists, attaching the smaller node to the merged list and recursively merging the rest. If one list is empty, it directly returns the other list as the merged result.

### Code-2 (C++)

```cpp
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
        if(list1 == NULL) return list2;
        if(list2 == NULL) return list1;
        if(list1->val <= list2->val){
            list1->next = mergeTwoLists(list1->next, list2);
            return list1;
        } else {
            list2->next = mergeTwoLists(list1, list2->next);
            return list2;
        }
    }
};
```

### Time Complexity:
- **O(n+m):** where n and m are the lengths of the two lists.

### Space Complexity:
- **O(n+m):** due to recursion stack.
### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>