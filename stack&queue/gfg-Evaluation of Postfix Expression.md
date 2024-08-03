# [Evaluation of Postfix Expression](https://www.geeksforgeeks.org/problems/evaluation-of-postfix-expression1735/1)

![](https://badgen.net/badge/Level/Easy/green)

Given string S representing a postfix expression, the task is to evaluate the expression and find the final value. Operators will only include the basic arithmetic operators like *, /, + and -.

### Approach Used :

-   Traverse each character of the postfix expression:
    -   If the character is an operand, push it onto the stack.
    -   If the character is an operator, pop the top two operands from the stack, apply the operator to these operands, and push the result back onto the stack.
-   At the end of the traversal, the stack will contain the final result of the postfix expression.

### Code (C++)

```cpp
class Solution {
public:
    // Function to evaluate a postfix expression.
    int evaluatePostfix(std::string S) {
        std::stack<int> st;
        
        for (char c : S) {
            // If the character is an operand, push it to the stack
            if (isdigit(c)) {
                st.push(c - '0'); // convert char to int
            } else {
                // If the character is an operator, pop two operands from the stack
                int val2 = st.top();
                st.pop();
                int val1 = st.top();
                st.pop();
                
                // Perform the operation and push the result back onto the stack
                switch (c) {
                    case '+': st.push(val1 + val2); break;
                    case '-': st.push(val1 - val2); break;
                    case '*': st.push(val1 * val2); break;
                    case '/': st.push(val1 / val2); break;
                }
            }
        }
        
        // The final result will be at the top of the stack
        return st.top();
    }
};
```

### Time Complexity:
- **O(n):** we traverse each character of the input string exactly once.

### Space Complexity:
- **O(n):** In the worst case, the stack may hold all operands 


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>