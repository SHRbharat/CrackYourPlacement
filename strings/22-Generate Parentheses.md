# [22. Generate Parentheses](https://leetcode.com/problems/generate-parentheses/description/)

![](https://badgen.net/badge/Level/Medium/yellow)

Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.

### Approach Used :

-   Use a recursive backtracking approach to build well-formed parentheses strings by ensuring that the number of closing parentheses never exceeds the number of opening ones. The recursion stops when the length of the string matches 2 * n, the total number of parentheses.


### Code (C++)

```cpp
class Solution {
public:
    vector<string> generateParenthesis(int n) {
        vector<string> result;
        generate(result, "", 0, 0, n);
        return result;
    }
    
private:
    void generate(vector<string>& result, string current, int open, int close, int n) {
        if (current.length() == 2 * n) {
            result.push_back(current);
            return;
        }
        
        if (open < n) {
            generate(result, current + '(', open + 1, close, n);
        }
        if (close < open) {
            generate(result, current + ')', open, close + 1, n);
        }
    }
};
```

### Time Complexity:
- **O(4^n / √n):**  where n is the number of pairs. This is because there are Catalan(n) valid combinations, and the number of such combinations grows exponentially.

### Space Complexity:
- **O(4^n / √n):**  for the result storage, as it stores all valid combinations. Additionally, the recursion stack requires O(n) space due to the depth of recursion, but this is overshadowed by the result storage complexity.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>