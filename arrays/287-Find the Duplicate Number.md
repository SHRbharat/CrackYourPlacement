```
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

### Time Complexity:

1. **Sorting the array:**
   - The sorting operation `sort(nums.begin(), nums.end())` has a time complexity of \(O(n \log n)\), where \(n\) is the number of elements in the array.
   
2. **Iterating through the array:**
   - The loop `for(int x : nums)` iterates through the array once, which has a time complexity of \(O(n)\).

Therefore, the overall time complexity of the provided solution is dominated by the sorting step, resulting in \(O(n \log n)\).

### Space Complexity:

1. **Sorting the array:**
   - The `sort` function requires \(O(1)\) extra space for the sorting itself if we consider in-place sorting algorithms like heapsort. However, many common sorting algorithms (like quicksort or mergesort) can have \(O(\log n)\) space complexity due to recursion stack space.
   
2. **Auxiliary space:**
   - The space used for variables (`prev` and `x`) is \(O(1)\).

Therefore, the overall space complexity is \(O(1)\) to \(O(\log n)\), depending on the sorting algorithm used.

```
Floyd's Tortoise and Hare Algorithm
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

### Explanation:

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

This algorithm efficiently finds the repeated number in linear time `O(n)` with constant extra space `O(1)`.
