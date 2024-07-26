# [20. Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)

![](https://badgen.net/badge/Level/Easy/green)

Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:
1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.
3. Every close bracket has a corresponding open bracket of the same type.

### Approach Used :

-   The approach uses a stack to track opening brackets and ensures each closing bracket matches the most recent unmatched opening bracket, popping from the stack if a match is found. If the stack is empty when a closing bracket is encountered or if there are unmatched brackets remaining in the stack at the end, the string is considered invalid.

### Code (C++)

```cpp
class Solution {
public:
    bool isValid(string s) {
        if(s == "")
            return true;
        stack<char> st;

        for(char x : s){
            if(x == '(' || x == '[' || x == '{'){
                st.push(x);
            }else{
                if(st.empty()) {
                    return false; // Stack is empty but a closing bracket is encountered
                }
                char top = st.top();
                if( (x == ')' && top != '(') || (x == '}' && top != '{') || (x == ']' && top != '[') ){
                    return false;
                }else{
                    st.pop();
                }
            }
        }
        
        if(st.empty()){
            return true;
        }
        return false;
    }
};
```

### Time Complexity:
- **O(n):** traverses the string once.

### Space Complexity:
- **O(n):** in worst case complete string can be in the stack.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>