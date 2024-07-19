# [28. Find the Index of the First Occurrence in a String](https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string/)

![](https://badgen.net/badge/Level/Easy/green)

Given two strings needle and haystack, return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

### Approach Used-1 (using substring):

-   extract a substring of length `n` at each iteration starting from the start of haystack string.

- check if the substring is equivalent to needle.

### Code-1 (C++)

```cpp
class Solution {
public:
  int strStr(string haystack, string needle) {
    const int m = haystack.length();
    const int n = needle.length();

    for (int i = 0; i < m - n + 1; i++)
      if (haystack.substr(i, n) == needle)
        return i;

    return -1;
  }
};
```

### Time Complexity:
- **O(n.m):** outer loop runs for m-n+1 times , and for each iteration substring creation takes O(n) time , then comparison also takes O(n) time resuting in `O((m-n+1).n)` time.

### Space Complexity:
- **O(n):** The substr method creates a new string of length n in each iteration, which takes O(n) space.

### Approach Used-2 (matching manually):

-   This solution iteratively checks each possible starting position in the haystack for the needle by comparing characters one by one. If the needle is found, it returns the starting index; otherwise, it returns -1.

### Code-2 (C++)

```cpp
class Solution {
public:
    int strStr(string haystack, string needle) {
        int m = haystack.size();
        int n = needle.size();
        
        if (n == 0) return 0; 
        for (int i = 0; i < m - n + 1; ++i) {
            int j;
            for (j = 0; j < n; ++j) {
                if (haystack[i + j] != needle[j]) {
                    break;
                }
            }
            if (j == n) {
                return i; 
            }
        }
        return -1;  
    }
};
```

### Time Complexity:
- **O(n.m):** outer loop runs for m-n+1 times , and for each iteration comparison takes O(n) time resuting in `O((m-n+1).n)` time.

### Space Complexity:
- **O(1):** no extra space is used.

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>