# [680. Valid Palindrome II](https://leetcode.com/problems/valid-palindrome-ii/)

![](https://badgen.net/badge/Level/Easy/green)

Given a string s, return true if the s can be palindrome after deleting at most one character from it.

### Approach Used :

-   Use two pointers to check if a string is a palindrome. If a mismatch occurs, check if removing either the left or right character can result in a palindrome.

### Code (C++)

```cpp
class Solution {
public:
    bool validPalindrome(string s) {
        int left = 0, right = s.size() - 1;
        
        while (left < right) {
            if (s[left] != s[right]) {
                // Try skipping either the left character or the right character
                return isPalindrome(s, left + 1, right) || isPalindrome(s, left, right - 1);
            }
            left++;
            right--;
        }
        
        return true;
    }
    
private:
    bool isPalindrome(const string& s, int left, int right) {
        while (left < right) {
            if (s[left] != s[right]) {
                return false;
            }
            left++;
            right--;
        }
        return true;
    }
};

```

### Time Complexity:
- **O(n):** string is traversed once

### Space Complexity:
- **O(1):** no extra space is used.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>