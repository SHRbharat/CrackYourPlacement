# [628. Maximum Product of Three Numbers](https://leetcode.com/problems/maximum-product-of-three-numbers/)

![](https://badgen.net/badge/Level/Easy/green)

Given an integer array nums, find three numbers whose product is maximum and return the maximum product.

### Approach Used-1 (using sorting):

-   The approach sorts the array and considers two potential maximum products: the product of the three largest numbers or the product of the two smallest (possibly negative) numbers and the largest number. The final result is the maximum of these potential products.

### Code-1 (C++)

```cpp
class Solution {
public:
    int maximumProduct(vector<int>& nums) {
        sort(nums.begin(), nums.end());

        int prod;
        int n = nums.size();
        
        if (n == 3) {
            prod = nums[0] * nums[1] * nums[2];
        } else {
            int p1 = nums[n-3] * nums[n-2] * nums[n-1];
            int p2 = nums[0] * nums[1] * nums[n-1];
            
            prod = max(p1, p2);
        }

        return prod;
    }
};
```

### Time Complexity:
- **O(nlogn):** due to sorting

### Space Complexity:
- **O(1):** no extra space is used.

### Approach Used-2 (without sorting):

-   This approach iterates through the array once to find the two smallest and three largest numbers. It then calculates and returns the maximum product between the product of the three largest numbers and the product of the largest number with the two smallest (potentially negative) numbers.

### Code-2 (C++)

```cpp
class Solution {
 public:
  int maximumProduct(vector<int>& nums) {
    int min1 = INT_MAX;  // the minimum
    int min2 = INT_MAX;  // the second minimum
    int max1 = INT_MIN;  // the maximum
    int max2 = INT_MIN;  // the second maximum
    int max3 = INT_MIN;  // the third maximum

    for (const int num : nums) {
      if (num <= min1) {
        min2 = min1;
        min1 = num;
      } else if (num <= min2) {
        min2 = num;
      }
      if (num >= max1) {
        max3 = max2;
        max2 = max1;
        max1 = num;
      } else if (num >= max2) {
        max3 = max2;
        max2 = num;
      } else if (num >= max3) {
        max3 = num;
      }
    }

    return max(max1 * min1 * min2, max1 * max2 * max3);
  }
};
```

### Time Complexity:
- **O(n):** traverses the array once.

### Space Complexity:
- **O(1):** no extra space is used.

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>