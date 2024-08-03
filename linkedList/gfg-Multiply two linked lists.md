# [Multiply two linked lists](https://www.geeksforgeeks.org/problems/multiply-two-linked-lists/1)

![](https://badgen.net/badge/Level/Easy/green)

Given elements as nodes of the two singly linked lists. The task is to multiply these two linked lists, say L1 and L2.

### Approach Used :

-   Convert each linked list to a number: Traverse each linked list to construct the corresponding number.
-   Multiply the numbers: Multiply the two numbers obtained from the linked lists.

### Code (C++)

```cpp
class solution {
public:
    const int MOD = 1000000007;
    
    // Helper function to convert a linked list to a number
    long long listToNumber(Node* head) {
        long long number = 0;
        while (head != nullptr) {
            number = (number * 10 + head->data) % MOD; // Keep number within MOD
            head = head->next;
        }
        return number;
    }
    
    // Function to multiply two linked lists
    long long multiplyTwoLists(Node* first, Node* second) {
        long long num1 = listToNumber(first);
        long long num2 = listToNumber(second);
        return (num1 * num2) % MOD; // Return result modulo MOD
    }
};
```

### Time Complexity:
- **O(n + m):** traverses both lists once

### Space Complexity:
- **O(1):** no extra space is used.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>