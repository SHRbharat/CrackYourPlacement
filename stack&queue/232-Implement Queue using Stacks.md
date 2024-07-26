# [232. Implement Queue using Stacks](https://leetcode.com/problems/implement-queue-using-stacks/)

![](https://badgen.net/badge/Level/Easy/green)

Implement a first in first out (FIFO) queue using only two stacks. The implemented queue should support all the functions of a normal queue (push, peek, pop, and empty).

### Approach Used :

-   The `MyQueue` class implements a queue using two stacks.

### Code (C++)

```cpp
class MyQueue {
    stack<int> main;
    stack<int> sec;
public:
    MyQueue() {
        // Constructor
    }
    
    void push(int x) {
        main.push(x);
    }
    
    int pop() {
        //transfer all to secondary stack
        if (sec.empty()) {
            while (!main.empty()) {
                sec.push(main.top());
                main.pop();
            }
        }
        int x = sec.top();
        sec.pop();
        return x;
    }
    
    int peek() {
        //transfer all to secondary stack
        if (sec.empty()) {
            while (!main.empty()) {
                sec.push(main.top());
                main.pop();
            }
        }
        return sec.top();
    }
    
    bool empty() {
        return main.empty() && sec.empty();
    }
};
```

### Time Complexity:
- **push    : O(1):** pushes on top of stack.
- **pop     : O(1):** In the worst case, elements are moved from main to sec which takes O(n) time. However, each element is moved only once from main to sec, making the amortized time complexity O(1).
- **peek    : O(1):** the amortized time complexity is O(1).
- **empty   : O(1):**

### Space Complexity:
- **O(n):** same number of elements are stored onto stack.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>