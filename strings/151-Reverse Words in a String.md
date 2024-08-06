# [151. Reverse Words in a String](https://leetcode.com/problems/reverse-words-in-a-string/description/)

![](https://badgen.net/badge/Level/Medium/yellow)

Given an input string s, reverse the order of the words.

A word is defined as a sequence of non-space characters. The words in s will be separated by at least one space.

Return a string of the words in reverse order concatenated by a single space.

Note that s may contain leading or trailing spaces or multiple spaces between two words. The returned string should only have a single space separating the words. Do not include any extra spaces.

### Approach Used :

-   Use a stringstream to extract words from the input string, store them in a vector, reverse the vector, and concatenate the words with a single space between them to form the final result.

### Code (C++)

```cpp
class Solution {
public:
    string reverseWords(string s) {
        // Remove leading and trailing spaces and normalize multiple spaces to a single space
        stringstream ss(s);
        string word;
        vector<string> words;
        
        // Read words from the stream
        while (ss >> word) {
            words.push_back(word);
        }
        
        // Build the result string from the reversed words
        string result;
        for (int i = words.size() - 1; i >= 0; i--) {
            result += words[i];
            if (i > 0) {
                result += ' ';
            }
        }
        
        return result;
    }
};
```

### Time Complexity:
- **O(n):** where n is the length of the input string. This includes parsing the string, storing the words, and constructing the final reversed string.

### Space Complexity:
- **O(n):** due to the additional space required for storing the words in a vector and constructing the result string.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>