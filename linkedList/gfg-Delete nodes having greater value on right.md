# [Delete nodes having greater value on right](https://www.geeksforgeeks.org/problems/delete-nodes-having-greater-value-on-right/1)

![](https://badgen.net/badge/Level/Easy/green)

Given a singly linked list, remove all the nodes in the list which have any node on their right whose value is greater. (Not just immediate Right , but entire List on the Right)

### Approach Used :

-   Reverse the Linked List
-   Process Nodes
-   Reverse the List Again:

### Code (C++)

```cpp
class Solution
{
    public:
    Node *compute(Node *head)
    {
        // your code goes here
        head=rev(head);
        int max=head->data;
        Node*curr=head->next;
        Node*prev=head;
        
        while(curr!=NULL){
            if(curr->data>=max){
                prev=curr;  //deleting prev
                max=curr->data; //storing max val of curr in max then return maxval
            }
            else{
                prev->next=curr->next; //when curr data is < max make two jumps
            }
            curr=curr->next;
        }
        return rev(head);
    }
    Node *rev( Node *head ){
        Node *curr = head ;
        Node *prev = nullptr ;
        Node*temp = nullptr ;
        
        while( curr != NULL ){
            temp = curr->next ;
            curr->next = prev ;
            prev = curr ;
            curr = temp ;
        }
        return prev;
    }
    
};
```

### Time Complexity:
- **O(n):** each node is processed constant number of times

### Space Complexity:
- **O(1):** no extra space is used.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>