# [169. Majority Element](https://leetcode.com/problems/majority-element/)

![](https://badgen.net/badge/Level/Easy/green)

Given an array nums of size n, return the majority element.

The majority element is the element that appears more than ⌊n / 2⌋ times. You may assume that the majority element always exists in the array.

### Approach Used-1:

-   create a frequecy couter using hash map.
-   check if any element has majority frequency

### Code-1 (C++)

```cpp
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        unordered_map<int,int> freq;
        for(auto x:nums){
            freq[x]++;
        }

        int maj = nums.size()/2;
        for(auto x : freq){
            if(x.second > maj){
                maj = x.first;
                break;
            }
        }

        return maj;
    }
};
```

### Time Complexity:
- **O(n):** first for loop runs for n iterations and second in worst case performs n iterations

### Space Complexity:
- **O(n):** space created for frequency counter

### Approach Used-2(Boyer-Moore Voting Algorithm):

-   The Boyer-Moore Voting Algorithm is based on the observation that if we pair up different elements and cancel them out, the majority element will still remain. This works because the majority element appears more than half the time, so it cannot be completely canceled out by pairing with other elements.
-   We iterate through the array. For each element num:
    -If count is 0, we set the current element num as the candidate.
    -We increment count if num is the same as candidate.
    -We decrement count if num is different from candidate.

### Code-2 (C++)

```cpp
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        int count = 0;
        int candidate = 0;

        //Find a candidate for the majority element
        for (int num : nums) {
            if (count == 0) {
                candidate = num;
            }
            count += (num == candidate) ? 1 : -1;
        }

        //Verify the candidate (optional if we assume the majority element always exists)
        
        // count = 0;
        // for (int num : nums) {
        //     if (num == candidate) {
        //         count++;
        //     }
        // }
        // if (count > nums.size() / 2) {
        //     return candidate;
        // }

        return candidate;
    }
};

```

### Time Complexity:
- **O(n):** first for loop runs for n iterations and second in worst case performs n iterations (optional).

### Space Complexity:
- **O(n):** no extra space is used.

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>