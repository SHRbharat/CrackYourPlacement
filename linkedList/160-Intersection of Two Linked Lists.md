# [160. Intersection of Two Linked Lists](https://leetcode.com/problems/intersection-of-two-linked-lists/)

![](https://badgen.net/badge/Level/Easy/green)

Given the heads of two singly linked-lists headA and headB, return the node at which the two lists intersect. If the two linked lists have no intersection at all, return null.

### Approach Used-1 (difference in length of lists) :

-  First, determine the lengths of both linked lists and align their starting points by advancing the pointer of the longer list by the length difference. Then, traverse both lists simultaneously to find the intersection node by comparing the nodes at each step. 

### Code-1 (C++)

```cpp
class Solution {
public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        // Calculate the lengths of both linked lists
        int lenA = 0, lenB = 0;
        ListNode* iteA = headA;
        ListNode* iteB = headB;

        while (iteA) {
            lenA++;
            iteA = iteA->next;
        }

        while (iteB) {
            lenB++;
            iteB = iteB->next;
        }

        // Reset the iterators to the start of each list
        iteA = headA;
        iteB = headB;

        // Advance the iterator of the longer list by the difference in lengths
        if (lenA > lenB) {
            for (int i = 0; i < lenA - lenB; i++) {
                iteA = iteA->next;
            }
        } else {
            for (int i = 0; i < lenB - lenA; i++) {
                iteB = iteB->next;
            }
        }

        // Traverse both lists in tandem to find the intersection node
        while (iteA && iteB) {
            if (iteA == iteB) {
                return iteA;
            }
            iteA = iteA->next;
            iteB = iteB->next;
        }

        return nullptr; // No intersection
    }
};
```

### Time Complexity:
- **O(n+m):** This is because we traverse each list to determine their lengths and then traverse the lists again to find the intersection.

### Space Complexity:
- **O(1):** no extra space is used.

### Approach Used-2 (two pointer technique) :

-  Use two pointers starting at the heads of headA and headB. Traverse both lists simultaneously, switching each pointer to the head of the other list when it reaches the end, ensuring that both pointers traverse equal lengths and meet at the intersection node or at the end (nullptr) if there is no intersection.

### Code-2 (C++)

```cpp
class Solution {
public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        if (!headA || !headB) return nullptr;

        ListNode *a = headA, *b = headB;
        
        // Traverse both lists, switching heads when reaching the end
        while (a != b) {
            a = a ? a->next : headB;
            b = b ? b->next : headA;
        }

        return a; // a or b will be the intersection node or nullptr if no intersection
    }
};
```

### Time Complexity:
- **O(n+m):** This is because each pointer traverses each list exactly once.

### Space Complexity:
- **O(1):** no extra space is used.

### Approach Used-3 (hashing) :

-  First, traverse the first linked list (headA) and store each node in a hash set. Then, traverse the second linked list (headB), checking each node against the hash set to find the first common node, which is the intersection point.

### Code-3 (C++)

```cpp
class Solution {
public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        if (!headA || !headB) return nullptr;

        //hash list A
        unordered_set<ListNode*> nodes;
        
        ListNode* current = headA;
        while (current) {
            nodes.insert(current);
            current = current->next;
        }

        current = headB;
        while (current) {
            //if node of list 2 found in hash set
            if (nodes.count(current)) {
                return current;
            }
            current = current->next;
        }

        return nullptr; 
    }
};
```

### Time Complexity:
- **O(n+m):** This is because we traverse both lists once.

### Space Complexity:
- **O(n):** This is due to the additional space required for the hash set to store the nodes of the first list.

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>