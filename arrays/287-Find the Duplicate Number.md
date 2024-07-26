# [287-find-the-duplicate-number](https://leetcode.com/problems/find-the-duplicate-number/)

![](https://badgen.net/badge/Level/Medium/yellow)

Given an array of integers nums containing n + 1 integers where each integer is in the range [1, n] inclusive.
There is only one repeated number in nums, return this repeated number.
You must solve the problem without modifying the array nums and uses only constant extra space.

### Approach Used - 1:
- Sorting the array and then iterating through it to find the duplicate element.

### Code-1 (C++)

```cpp
class Solution {
public:
    int findDuplicate(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        
        int prev = INT_MIN;
        for(int x:nums){
            if(x == prev)
                break;
            prev = x;
        }
        return prev;
    }
};
```

### Time Complexity:
- **O(nlog n):** The sorting operation has a time complexity of O(nlog n) & the loop iterates through the array once, which has a time complexity of O(n).
### Space Complexity:
- **O(1) to O(log n):** sorting algorithms can have O(log n) space complexity due to recursion stack space.

### Approach Used - 2 (Floyd's Tortoise and Hare Algorithm):
1. **Initialization:**
   - `slow` and `fast` pointers are both initialized to the first element of the array.

2. **Finding the Intersection Point:**
   - The `slow` pointer moves one step at a time: `slow = nums[slow]`.
   - The `fast` pointer moves two steps at a time: `fast = nums[nums[fast]]`.
   - The loop continues until `slow` equals `fast`, indicating a cycle is detected.

3. **Finding the Entrance to the Cycle:**
   - Reset the `slow` pointer to the beginning of the array.
   - Move both `slow` and `fast` pointers one step at a time: `slow = nums[slow]` and `fast = nums[fast]`.
   - The point where `slow` and `fast` meet again is the entrance to the cycle, which is the repeated number.

### Code-2 (C++)

```cpp
class Solution {
public:
    int findDuplicate(vector<int>& nums) {
        // Initialize the slow and fast pointers
        int slow = nums[0];
        int fast = nums[0];
        
        // Phase 1: Finding the intersection point of the two runners
        do {
            slow = nums[slow];
            fast = nums[nums[fast]];
        } while (slow != fast);
        
        // Phase 2: Finding the entrance to the cycle (the repeated number)
        slow = nums[0];
        while (slow != fast) {
            slow = nums[slow];
            fast = nums[fast];
        }
        
        return slow;
    }
};
```

### Time Complexity:
- **O(n):** The loop iterates through the array once.

### Space Complexity:
- **O(1):** No extra space is used.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>