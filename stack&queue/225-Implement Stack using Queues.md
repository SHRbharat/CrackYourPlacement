# [225. Implement Stack using Queues](https://leetcode.com/problems/implement-stack-using-queues/)

![](https://badgen.net/badge/Level/Easy/green)

Implement a last-in-first-out (LIFO) stack using only two queues. The implemented stack should support all the functions of a normal stack (push, top, pop, and empty).

### Approach Used (using two queues):

-   pop():
    -   Transfer all elements from q1 to q2 except the last element.
    -   The last element in q1 is the top element of the stack, which is removed and returned.
    -   Swap the names of q1 and q2 to maintain the invariant that q1 is always the main queue.

### Code (C++)

```cpp
class MyStack {
private:
    std::queue<int> q1;
    std::queue<int> q2;
    int topElement;

public:
    MyStack() {
        
    }
    
    void push(int x) {
        q1.push(x);
        topElement = x;
    }
    
    int pop() {
        while (q1.size() > 1) {
            topElement = q1.front();
            q2.push(topElement);
            q1.pop();
        }
        int poppedElement = q1.front();
        q1.pop();
        
        // Swap names of q1 and q2 (not contents)
        std::swap(q1, q2);
        
        return poppedElement;
    }
    
    int top() {
        return topElement;
    }
    
    bool empty() {
        return q1.empty();
    }
};
```

### Time & Space Complexity:
| Method      | Time Complexity | Space Complexity |
|-------------|-----------------|------------------|
| push(int x) | O(1)            | O(1)             |
| pop()       | O(n)            | O(1)             |
| top()       | O(1)            | O(1)             |
| empty()     | O(1)            | O(1)             |

### Approach Used (using single queue):

-   This approach uses a single queue to simulate a stack by rotating the elements within the queue each time a new element is pushed, ensuring the last pushed element is always at the front of the queue. This allows pop and top operations to be performed in constant time.

### Code (C++)

```cpp
class MyStack {
 private:
  queue<int> q;
 public:
  void push(int x) {
    q.push(x);
    for (int i = 0; i < q.size() - 1; ++i) {
      q.push(q.front());
      q.pop();
    }
  }

  int pop() {
    const int val = q.front();
    q.pop();
    return val;
  }

  int top() {
    return q.front();
  }

  bool empty() {
    return q.empty();
  }
};
```

### Time & Space Complexity:
| Method      | Time Complexity | Space Complexity |
|-------------|-----------------|------------------|
| push(int x) | O(n)            | O(1)             |
| pop()       | O(1)            | O(1)             |
| top()       | O(1)            | O(1)             |
| empty()     | O(1)            | O(1)             |


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>