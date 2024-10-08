# [26-remove-duplicates-from-sorted-array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

![](https://badgen.net/badge/Level/Easy/green)

Given an integer array nums sorted in non-decreasing order, remove the duplicates in-place such that each unique element appears only once. The relative order of the elements should be kept the same. Then return the number of unique elements in nums.

Consider the number of unique elements of nums to be k, to get accepted, you need to do the following things:

Change the array nums such that the first k elements of nums contain the unique elements in the order they were present in nums initially. The remaining elements of nums are not important as well as the size of nums.
Return k.

### Approach Used :
1. **Initialization:**
   - Check if `nums` is empty. If it is, return 0 since there are no elements to process.
   - Initialize `k` to 1, which represents the position where the next unique element should be placed.

2. **Iterating through the array:**
   - Start iterating from the second element (index 1) to the end of the array.
   - For each element, check if it is different from the previous element (`nums[i] != nums[i - 1]`).
   - If it is different, it is a unique element, and it should be placed at the `k`-th position in the array. Then, increment `k`.

3. **Returning the result:**
   - After the loop, `k` will be the count of unique elements, and the first `k` elements in `nums` will be the unique elements in their original order.


### Code (C++)

```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        if (nums.empty()) {
            return 0;
        }

        int k = 1; // Index of the next unique element

        for (int i = 1; i < nums.size(); ++i) {
            if (nums[i] != nums[i - 1]) {
                nums[k] = nums[i];
                ++k;
            }
        }

        return k;
    }
};
```

### Time Complexity:
- **O(n):** The algorithm makes a single pass through the array.

### Space Complexity:
- **O(1):** The algorithm uses a constant amount of extra space.

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>