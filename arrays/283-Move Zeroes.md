# [283. Move Zeroes](https://leetcode.com/problems/move-zeroes/)

![](https://badgen.net/badge/Level/Easy/green)

Given an integer array nums, move all 0's to the end of it while maintaining the relative order of the non-zero elements.

Note that you must do this in-place without making a copy of the array.

### Approach Used :

-  we can use the two-pointer technique , in which a `nonZeroIndex` pointer is used to track the position where the next non-zero element should be placed. 

- For each element in the array, if the element is non-zero, we place it at the position indicated by nonZeroIndex and increment nonZeroIndex.

- After placing all non-zero elements in their correct positions, we fill the remaining positions in the array with zeros.


### Code (C++)

```cpp
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        int nonZeroIndex = 0; // position for the next non-zero element

        // Move all non-zero elements to the front of the array
        for (int i = 0; i < nums.size(); i++) {
            if (nums[i] != 0) {
                nums[nonZeroIndex++] = nums[i];
            }
        }

        //Fill the remaining positions with zeros
        for (int i = nonZeroIndex; i < nums.size(); i++) {
            nums[i] = 0;
        }
    }
};
```

### Time Complexity:
- **O(n):** two for loops iterating over the array

### Space Complexity:
- **O(1):** no extra space is created.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>