# [496. Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/)

![](https://badgen.net/badge/Level/Easy/green)

The next greater element of some element x in an array is the first greater element that is to the right of x in the same array.

You are given two distinct 0-indexed integer arrays nums1 and nums2, where nums1 is a subset of nums2.

For each 0 <= i < nums1.length, find the index j such that nums1[i] == nums2[j] and determine the next greater element of nums2[j] in nums2. If there is no next greater element, then the answer for this query is -1.

Return an array ans of length nums1.length such that ans[i] is the next greater element as described above.

### Approach Used :

-   Use a decreasing stack to find the next greater element for each number in nums2.
-   Map each number in nums1 to its next greater element found in nums2, or -1 if no such element exists.

1.  Traverse nums2:
    -   For each number in nums2, check if the stack is not empty and the top element of the stack is less than the current number.This means the current number is the next greater element for the top element of the stack.
    -   Pop elements from the stack while they are less than the current number and map them to the current number in nextGreaterMap.
    -   Push the current number onto the stack to maintain the decreasing order.
2.  Build the Result for nums1:
    -   For each number in nums1, look up its next greater element in nextGreaterMap.
    -   If the number exists in the map, add its next greater element to the result.
    -   If the number does not exist in the map, add -1 to the result, indicating there is no next greater element in nums2 for that number.
### Example:
Consider nums1 = [4, 1, 2] and nums2 = [1, 3, 4, 2].

1. Process nums2 with the stack.
    -   Push 1 onto the stack.
    -   3 is greater than 1, so map 1 to 3 and pop 1. Push 3.
    -   4 is greater than 3, so map 3 to 4 and pop 3. Push 4.
    -   2 is not greater than 4, so just push 2.
2. Result mapping.
    -   For 4 in nums1, no entry in nextGreaterMap, so append -1.
    -   For 1 in nums1, map entry is 3, so append 3.
    -   For 2 in nums1, no entry in nextGreaterMap, so append -1.
3.  Final result: [-1, 3, -1].
### Code (C++)

```cpp
class Solution {
public:
    vector<int> nextGreaterElement(vector<int>& nums1, vector<int>& nums2) {
        vector<int> result;
        unordered_map<int, int> nextGreaterMap;
        stack<int> decreasingStack;

        // Traverse nums2 to populate the next greater element map
        for (const int num : nums2) {
            while (!decreasingStack.empty() && decreasingStack.top() < num) {
                nextGreaterMap[decreasingStack.top()] = num;
                decreasingStack.pop();
            }
            decreasingStack.push(num);
        }

        // Populate the result for nums1 using the next greater element map
        for (const int num : nums1) {
            if (const auto it = nextGreaterMap.find(num); it != nextGreaterMap.end()) {
                result.push_back(it->second);
            } else {
                result.push_back(-1);
            }
        }

        return result;
    }
};

```

### Time Complexity:
- **O(m+n):** lengths o two arrays , each element in nums2 is pushed and popped from the stack exactly once. Therefore, the time complexity for processing nums2 is O(n). For each element in nums1, we perform a constant-time lookup in the map, resulting in O(m) time complexity.

### Space Complexity:
- **O(n):** In the worst case, all elements of nums2 could be pushed onto the stack, resulting in O(n) space complexity. The map nextGreaterMap could store at most n elements if every element in nums2 has a next greater element. Hence, the map also has a space complexity of O(n).


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>
