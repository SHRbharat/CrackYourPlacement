# [Permutations in array](https://www.geeksforgeeks.org/problems/permutations-in-array1747/1)

![](https://badgen.net/badge/Level/Easy/green)

Given two arrays of equal size N and an integer K. The task is to check if after permuting both arrays, we get sum of their corresponding element greater than or equal to k i.e Ai + Bi >= K for all i (from 0 to N-1). Return true if possible, else false.

### Approach Used :

-   sort the arrays in asecending and descending order than compare the corresponding elements of both arrays.

### Code (C++)

```cpp
class Solution {
  public:
    bool isPossible(long long a[], long long b[], int n, long long k) {
        sort(a, a + n);
        sort(b, b + n, greater<long long>());
        
        for (int i = 0; i < n; ++i) {
            if (a[i] + b[i] < k) {
                return false;
            }
        }
        
        return true;
    }
};
```

### Time Complexity:
- **O(nlogn):** dominated by sorting 

### Space Complexity:
- **O(1):** no extra space is used.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>