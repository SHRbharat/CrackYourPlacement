# [14. Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/)

![](https://badgen.net/badge/Level/Easy/green)

Write a function to find the longest common prefix string amongst an array of strings.
If there is no common prefix, return an empty string "".

### Approach Used :

-   The vertical scanning approach compares characters at each position across all strings, stopping when a mismatch is found, and returns the substring up to that point. If all characters match in the range of the first string's length, the first string is returned as the longest common prefix.


### Code (C++)

```cpp
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        if (strs.empty()) return "";
        
        // Iterate through the characters of the first string
        for (int i = 0; i < strs[0].size(); ++i) {
            char c = strs[0][i];
            // Compare the character with the corresponding character in the other strings
            for (int j = 1; j < strs.size(); ++j) {
                // If the current string is shorter or the characters don't match, return the result
                if (i >= strs[j].size() || strs[j][i] != c) {
                    return strs[0].substr(0, i);
                }
            }
        }
        
        return strs[0];
    }
};
```

### Time Complexity:
- **O(S):** where S is the sum of all characters in all strings. In the worst case, all characters of all strings are checked.

### Space Complexity:
- **O(1):** no extra space is used.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>