Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.
https://leetcode.com/problems/two-sum/description/

class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int,int> index; //key : elements , value : index
        int n = nums.size() , comple;
        for(int i=0;i<n;i++){
            comple = target - nums[i];

            //check for complemwnt in map
            if(index.find(comple) != index.end())
                return {i , index[comple]};

            //update the map
            index[nums[i]] = i;
        }

        return {};
    }
};

To solve the problem of finding two indices in an array that add up to a given target, we can use a hash map (unordered_map in C++) to efficiently track the indices of the elements as we iterate through the array. This approach allows us to find the solution in linear time.

### Explanation:

1. **Initialization:**
   - Use an `unordered_map` (numMap) to store the elements of the array and their indices as we iterate through the array.

2. **Iterating through the array:**
   - For each element `nums[i]`, calculate its complement with respect to the target (`complement = target - nums[i]`).
   - Check if the complement already exists in the map. If it does, that means we have found the two indices that add up to the target.
     - Return the indices of the complement and the current element (`{numMap[complement], i}`).
   - If the complement does not exist in the map, store the current element and its index in the map (`numMap[nums[i]] = i`).

3. **Return the result:**
   - If a solution is found, the function returns the indices. If no solution is found (which is not the case according to the problem statement), the function would return an empty vector.

### Time Complexity:

- **O(n):** The algorithm iterates through the array once, performing constant-time operations (insertions and lookups) in the hash map.

### Space Complexity:

- **O(n):** The hash map stores up to `n` elements in the worst case.
