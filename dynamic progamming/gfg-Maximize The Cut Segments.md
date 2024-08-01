# [Maximize The Cut Segments](https://www.geeksforgeeks.org/problems/cutted-segments1642/1/)

![](https://badgen.net/badge/Level/Medium/yellow)

Given an integer n denoting the Length of a line segment. You need to cut the line segment in such a way that the cut length of a line segment each time is either x , y or z. Here x, y, and z are integers.
After performing all the cut operations, your total number of cut segments must be maximum.

Note: if no segment can be cut then return 0.

### Approach Used :

-   Dynamic Programming (DP) Table:
    -   Use a 1D DP table dp where dp[i] represents the maximum number of segments you can get from a line segment of length i.
-   Initialization:
    -   Initialize dp[0] to 0 because a line segment of length 0 can be divided into 0 segments.
-   DP Transition:
    -   For each length i from 1 to n, update dp[i] based on the lengths x, y, and z. Specifically, update dp[i] using:
        -   dp[i] = max(dp[i - x], dp[i - y], dp[i - z]) + 1
    -   Ensure that i - x, i - y, and i - z are non-negative before accessing dp[i - x], dp[i - y], and dp[i - z].
-   Result:
    -   The result will be in dp[n], which represents the maximum number of segments for a line segment of length n.

### Code (C++)

```cpp
class Solution {
public:
    int maximizeTheCuts(int n, int x, int y, int z) {
        vector<int> dp(n + 1, -1); // Initialize DP array with -1 (indicating impossible)
        dp[0] = 0; // Base case: 0 length line segment has 0 cuts

        for (int i = 1; i <= n; ++i) {
            if (i >= x && dp[i - x] != -1) {
                dp[i] = max(dp[i], dp[i - x] + 1);
            }
            if (i >= y && dp[i - y] != -1) {
                dp[i] = max(dp[i], dp[i - y] + 1);
            }
            if (i >= z && dp[i - z] != -1) {
                dp[i] = max(dp[i], dp[i - z] + 1);
            }
        }

        return dp[n] == -1 ? 0 : dp[n]; // If no valid cuts found, return 0
    }
};

```

### Time Complexity:
- **O(n):** The algorithm iterates through each length from 1 to n and performs constant-time updates for each length.

### Space Complexity:
- **O(n):** The space complexity is due to the DP array of size n + 1.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>