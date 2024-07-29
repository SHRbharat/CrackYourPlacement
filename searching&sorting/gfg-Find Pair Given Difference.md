# [Find Pair Given Difference](https://www.geeksforgeeks.org/problems/find-pair-given-difference1559/1)

![](https://badgen.net/badge/Level/Easy/green)

Given an array arr[] of size n and an integer x, return 1 if there exists a pair of elements in the array whose absolute difference is x, otherwise, return -1.

### Approach Used :

-   To solve the problem of finding if there exists a pair of elements in the array whose absolute difference is 
𝑥
x, we can use a hash set to store the elements of the array. This approach allows us to efficiently check for the existence of a complement value that forms the required difference with each element.


### Code (C++)

```cpp
class Solution {
public:
    int findPair(int n, int x, vector<int> &arr) {
        unordered_set<int> elements;
        
        for (int i = 0; i < n; ++i) {
            // Check if there is a pair with absolute difference x
            if (elements.find(arr[i] + x) != elements.end() || 
                elements.find(arr[i] - x) != elements.end()) {
                return 1;
            }
            // Add the current element to the set
            elements.insert(arr[i]);
        }
        
        return -1;
    }
};
```

### Time Complexity:
- **O(n):** as each element is traversed once.

### Space Complexity:
- **O(n):** in worst case all elements will be in hash set.

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>