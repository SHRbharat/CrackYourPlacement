# [Implement two stacks in an array](https://www.geeksforgeeks.org/problems/implement-two-stacks-in-an-array/1)

![](https://badgen.net/badge/Level/Easy/green)

Your task is to implement  2 stacks in one array efficiently. You need to implement 4 methods.

twoStacks : Initialize the data structures and variables to be used to implement  2 stacks in one array.
push1 : pushes element into first stack.
push2 : pushes element into second stack.
pop1 : pops element from first stack and returns the popped element. If first stack is empty, it should return -1.
pop2 : pops element from second stack and returns the popped element. If second stack is empty, it should return -1.

### Approach Used :

-   One stack starts from the beginning of the array and grows towards the end, while the other stack starts from the end and grows towards the beginning.

### Code (C++)

```cpp
class twoStacks {
private:
    std::vector<int> arr;
    int top1, top2;
    int size;

public:
    // Constructor to initialize the data structures and variables
    twoStacks(int n = 100) { // default size of 100
        size = n;
        arr.resize(n);
        top1 = -1;
        top2 = n;
    }

    // Function to push an integer into the stack1
    void push1(int x) {
        if (top1 < top2 - 1) { // There is space between top1 and top2
            arr[++top1] = x;
        } else {
            std::cerr << "Stack Overflow" << std::endl;
        }
    }

    // Function to push an integer into the stack2
    void push2(int x) {
        if (top1 < top2 - 1) { // There is space between top1 and top2
            arr[--top2] = x;
        } else {
            std::cerr << "Stack Overflow" << std::endl;
        }
    }

    // Function to remove an element from top of the stack1
    int pop1() {
        if (top1 >= 0) {
            int x = arr[top1--];
            return x;
        } else {
            return -1; // Stack Underflow
        }
    }

    // Function to remove an element from top of the stack2
    int pop2() {
        if (top2 < size) {
            int x = arr[top2++];
            return x;
        } else {
            return -1; // Stack Underflow
        }
    }
};
```

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>