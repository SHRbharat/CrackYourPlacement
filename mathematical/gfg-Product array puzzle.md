# [Product array puzzle](https://www.geeksforgeeks.org/problems/product-array-puzzle4525/1)

![](https://badgen.net/badge/Level/Easy/green)

Given an array nums[] of size n, construct a Product Array P (of same size n) such that P[i] is equal to the product of all the elements of nums except nums[i].

### Approach Used :

-   *Calculate the Total Product :* Calculate the product of all non-zero elements in the array.
-   *Count Zeros :* Count the number of zeros in the array.
-   *Construct the Result Array :*
        -If there are more than one zero, the product for each position will be zero.
        -If there is exactly one zero, only the position corresponding to the zero in the original array will have the total product (of non-zero elements), while the rest will be zero.
        -If there are no zeros, the product for each position can be calculated by dividing the total product by the value at that position.

### Code (C++)

```cpp
class Solution {
public:
    vector<long long int> productExceptSelf(vector<long long int>& nums, int n) {
        long long int totalProduct = 1;
        int zeroCount = 0;
        
       for (auto x : nums) {
            if (x != 0) {
                totalProduct *= x;
            } else {
                zeroCount++;
            }
        }
        
        vector<long long int> res(n, 0);
        
        for (int i = 0; i < n; i++) {
            if (nums[i] == 0) {
                // If the current element is zero and there is exactly one zero
                if (zeroCount == 1) {
                    res[i] = totalProduct; // Product of all other elements
                }
                // If zeroCount > 1, res[i] remains 0
            } else {
                if (zeroCount == 0) {
                    // If there are no zeros
                    res[i] = totalProduct / nums[i];
                }
                // If zeroCount > 0, res[i] remains 0
            }
        }
        
        return res;
    }
};
```

### Time Complexity:
- **O(n):** both loops traverse the array once

### Space Complexity:
- **O(n):** for storing the product array.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>