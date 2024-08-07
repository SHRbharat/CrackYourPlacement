# [Word Wrap](https://www.geeksforgeeks.org/problems/word-wrap1646/1)

![](https://badgen.net/badge/Level/Hard/red)

Given an array nums[] of size n, where nums[i] denotes the number of characters in one word. Let K be the limit on the number of characters that can be put in one line (line width). Put line breaks in the given sequence such that the lines are printed neatly.
Assume that the length of each word is smaller than the line width. When line breaks are inserted there is a possibility that extra spaces are present in each line. The extra spaces include spaces put at the end of every line except the last one. 

You have to minimize the following total cost where total cost = Sum of cost of all lines, where cost of line is = (Number of extra spaces in the line)2.

### Approach Used :

-   Calculate the minimum cost of putting words from i to j in one line, if possible.
-   Use this cost to fill in the DP table iteratively.
-   Return the minimum cost stored in the DP table for arranging all words from the beginning.

### Code (C++)

```cpp
class Solution {
public:
    int solveWordWrap(vector<int> nums, int k) { 
        int n = nums.size();
        vector<int> dp(n, 0);
        vector<int> cost(n, 0);
        
        // Calculate cost of putting words from i to j in one line
        for (int i = n - 1; i >= 0; --i) {
            int length = -1; // Initialize length as -1 to account for the space before the first word
            dp[i] = INT_MAX; // Initialize dp[i] with a high value
            for (int j = i; j < n; ++j) {
                length += (nums[j] + 1); // Update length
                if (length > k) break; // If length exceeds the limit, break
                int currentCost = (j == n - 1) ? 0 : (k - length) * (k - length); // Cost for the current line
                if (j + 1 < n) currentCost += dp[j + 1]; // Add the cost of the rest
                dp[i] = min(dp[i], currentCost); // Find the minimum cost
            }
        }
        return dp[0]; // Return the minimum cost for the whole array
    }
};

```

### Time Complexity:
- **O(n<sup>2</sup>):** outer loop runs n times ,and inner loop runs n-i times in worst case.

### Space Complexity:
- **O(n):** We use a dp array of size n 


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>