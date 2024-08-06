# [Smallest window in a string containing all the characters of another string](https://www.geeksforgeeks.org/problems/smallest-window-in-a-string-containing-all-the-characters-of-another-string-1587115621/1)

![](https://badgen.net/badge/Level/Hard/red)

Given two strings S and P. Find the smallest window in the string S consisting of all the characters(including duplicates) of the string P.  Return "-1" in case there is no such window present. In case there are multiple such windows of same length, return the one with the least starting index.
Note : All characters are in Lowercase alphabets. 

### Approach Used :

-   To solve the problem of finding the smallest window in the string S that contains all characters of the string P, we can use the sliding window technique with two pointers. Here's the detailed approach and code implementation:
    -   Initialize variables:
        -   start and end to represent the sliding window.
        -   min_len to store the minimum length of the window found.
        -   min_start to store the starting index of the minimum window.
        -   count_p to store the frequency of characters in P.
        -   count_s to store the frequency of characters in the current window of S.
    -   Expand the window by moving the end pointer:
        -   For each character in S, increase its count in count_s.
        -   Check if the current character matches one in P and update a matched counter.
    -   Contract the window by moving the start pointer:
        -   When all characters in P are matched (matched == p.size()), try to minimize the window by moving the start pointer.
        -   Update min_len and min_start if a smaller window is found.
        -   Decrease the frequency of the character at start in count_s and adjust the matched counter if needed.
    -   Return the result:
        -   If a valid window is found, return the substring of S starting at min_start with length min_len.
        -   Otherwise, return "-1".

### Code (C++)

```cpp
class Solution {
public:
    string smallestWindow (string s, string p) {
        vector<int> count_p(128, 0);
        vector<int> count_s(128, 0);
        
        // Count frequency of each character in P
        for(char c : p) {
            count_p[c]++;
        }
        
        int start = 0, min_start = 0, min_len = INT_MAX, matched = 0;
        
        for(int end = 0; end < s.size(); end++) {
            char end_char = s[end];
            count_s[end_char]++;
            
            // Only increase matched if count of end_char in current window <= count in p
            if(count_s[end_char] <= count_p[end_char]) {
                matched++;
            }
            
            // When all characters are matched
            while(matched == p.size()) {
                // Update minimum length and start index if needed
                if(end - start + 1 < min_len) {
                    min_len = end - start + 1;
                    min_start = start;
                }
                
                char start_char = s[start];
                count_s[start_char]--;
                
                // Only decrease matched if count of start_char in current window < count in p
                if(count_s[start_char] < count_p[start_char]) {
                    matched--;
                }
                
                start++;
            }
        }
        
        return min_len == INT_MAX ? "-1" : s.substr(min_start, min_len);
    }
};

```

### Time Complexity:
- **O(m+n):** O(1) + O(m) + O(n) + O(n)

### Space Complexity:
- **O(1):** no extra space is used.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>