# [Subtraction in Linked List](https://www.geeksforgeeks.org/problems/subtraction-in-linked-list/1)

![](https://badgen.net/badge/Level/Hard/red)

You are given two linked lists that represent two large positive numbers. These two numbers are represented by the linked lists, subtract the smaller number from the larger one. Look at the examples to get a better understanding of the task.

### Approach Used :

-   The given approach subtracts two linked lists that represent large numbers. The solution involves reversing the linked lists, performing subtraction, and then reversing the result to get the correct order.

### Code (C++)

```cpp
class Solution {
public:
    void add_at_end(Node *&head,int x)
    {
        static Node *rear=head;
        if(head==NULL)
        {
            head=new Node(x);
            rear=head;
            return;
        }
        rear->next=new Node(x);
        rear=rear->next;
    }
    int reverse(Node *&head)
    {
        Node *curr=head;
        Node *next=NULL;
        Node *prev=NULL;
        int a=0;
        while(curr!=NULL)
        {
            next=curr->next;
            curr->next=prev;
            prev=curr;
            curr=next;
            a++;
        }
        head= prev;
        return a;
    }
    Node* subLinkedList(Node* head1, Node* head2) {
        // Your implementation of subLinkedList goes here
        // Make sure to return the head of the resulting linked list
       Node *head3=NULL;
       int a=head1->data;
       int b=head2->data;
      while(head1!=NULL && head1->data==0)head1=head1->next;
      while(head2!=NULL && head2->data==0)head2=head2->next;
      Node *_1c=head1;
      Node *_2c=head2;
      Node *h1=head1;
      Node *h2=head2;
      while((h1!=NULL && h2!=NULL)&& (_1c->data==_2c->data))
      {
          _1c=_1c->next;
          _2c=_2c->next;
          h1=h1->next;
          h2=h2->next;
      }
      if(h1==NULL && h2==NULL)
      {
          head3=new Node(0);
          return head3;
      }
       long long int count1=reverse(head1);
       long long int count2=reverse(head2);
       if(count1<count2)
       {
           Node *temp=head1;
           head1=head2;
           head2=temp;
       }
       else if(count1==count2)
       {
          if(_1c->data<_2c->data)
          {
              Node *temp=head1;
              head1=head2;
              head2=temp;
          }
       }
       Node *p=head1;
       Node *q=head2;
       int borrow=0;
       while(q!=NULL)
       {
           int sub=p->data-q->data-borrow;
           borrow=0;
           if(sub<0)
           {
              add_at_end(head3,sub+10);
               borrow=1;
           }
           else
           {
               add_at_end(head3,sub);
           }
           p=p->next;
           q=q->next;
       }
       while(p!=NULL)
       {
           int sum=p->data-borrow;
           borrow=0;
           if(sum<0)
           {
               add_at_end(head3,sum+10);
               borrow= 1;
           }
           else
           {
               add_at_end(head3,sum);
           }
           p=p->next;
       }
       reverse(head3);
       while(head3->data==0)
       {
           head3=head3->next;
           if(head3==NULL)
           {
               head3=new Node(0);
               return head3;
           }
       }
       return head3;
    }
};
```

### Time Complexity:
- **O(n + m):** The linked lists are traversed multiple times (to remove leading zeros, reverse, subtract, and reverse again), but each traversal is linear with respect to the size of the lists. 

### Space Complexity:
- **O(1):** no extra space is used.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>