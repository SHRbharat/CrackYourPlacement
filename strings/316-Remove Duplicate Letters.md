# [316. Remove Duplicate Letters](https://leetcode.com/problems/remove-duplicate-letters/)

![](https://badgen.net/badge/Level/Medium/yellow)

Given a string s, remove duplicate letters so that every letter appears once and only once. You must make sure your result is the smallest in lexicographical order among all possible results.

### Approach Used :

-   *Track Last Occurrences and Build Result:* Use an array to record the last occurrence of each character in the string and iterate through the string to build the result while ensuring each character appears only once and in the smallest lexicographical order by removing previously added characters that can still appear later.
-   *Maintain Original Order:* Ensure that characters are added to the result in the order they appear in the original string, using a stack-like approach to compare and remove characters dynamically.

### Code (C++)

```cpp
class Solution {
public:
    string removeDuplicateLetters(string s) {
        vector<int> lastIndex(26, 0); // last occurrence of each character
        vector<bool> seen(26, false); // whether a character is in the current result
        string res = "";

        // record the last occurrence of each character
        for (int i = 0; i < s.size(); i++) {
            lastIndex[s[i] - 'a'] = i;
        }

        for (int i = 0; i < s.size(); i++) {
            char c = s[i];
            if (seen[c - 'a']) continue; // if the character is already in the result, skip it
            
            // remove characters that are greater than the current character c
            // and can be found later in the string
            while (!res.empty() && res.back() > c && lastIndex[res.back() - 'a'] > i) {
                seen[res.back() - 'a'] = false;
                res.pop_back();
            }

            // add current character to the result and mark it as seen
            res += c;
            seen[c - 'a'] = true;
        }

        return res;
    }
};
```

### Time Complexity:
- **O(n):** This is because we make a single pass to record the last occurrence of each character and another pass to construct the result while possibly removing characters from the result.

### Space Complexity:
- **O(1):** no extra space is used.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>