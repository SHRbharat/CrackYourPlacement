# [01-Two Sum](https://leetcode.com/problems/two-sum/)

![](https://badgen.net/badge/Level/Medium/green)

Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.
You may assume that each input would have exactly one solution, and you may not use the same element twice.
You can return the answer in any order.

### Approach Used :

-   To solve the problem of finding two indices in an array that add up to a given target, we can use a hash map (unordered_map in C++) to efficiently track the indices of the elements as we iterate through the array.

- Use an `unordered_map` to store the elements of the array and their indices as we iterate through the array.

- For each element `nums[i]`, calculate its complement with respect to the target (`complement = target - nums[i]`).

- Check if the complement already exists in the map. If it does, that means we have found the two indices that add up to the target.
    - Return the indices of the complement and the current element (`{numMap[complement], i}`).
    - If the complement does not exist in the map, store the current element and its index in the map (`numMap[nums[i]] = i`).

### Code (C++)

```cpp
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
```

### Time Complexity:
- **O(n):** The algorithm iterates through the array once, performing constant-time operations (insertions and lookups) in the hash map.

### Space Complexity:
- **O(n):** The hash map stores up to `n` elements in the worst case.

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>