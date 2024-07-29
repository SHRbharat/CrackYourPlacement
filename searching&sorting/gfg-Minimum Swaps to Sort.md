# [Minimum Swaps to Sort](https://www.geeksforgeeks.org/problems/minimum-swaps/1)

![](https://badgen.net/badge/Level/Medium/yellow)

Given an array of n distinct elements. Find the minimum number of swaps required to sort the array in strictly increasing order.

### Approach Used :

-   To find the minimum number of swaps required to sort an array in strictly increasing order, we can leverage the concept of cycle detection in graphs. Each element in the array can be thought of as a node, and an edge can be drawn from node i to node j if the element at index i should be at index j in the sorted array.

-   *Pair Elements with Their Indices:* Create pairs of array elements and their indices.
-   *Sort the Pairs:* Sort these pairs based on the array elements.
-   *Detect Cycles:* Use the sorted positions to detect cycles. Each cycle in the graph represents a set of swaps needed to place each element in its correct position.
-   *Count Swaps:* The number of swaps required to sort the array is equal to the sum of 
(length_of_each_cycle−1).

### Code (C++)

```cpp
class Solution 
{
public:
    // Function to find the minimum number of swaps required to sort the array. 
    int minSwaps(vector<int>& nums)
    {
        int n = nums.size();
        vector<pair<int, int>> arrPos(n);
        
        // Pair array elements with their indices
        for (int i = 0; i < n; i++) {
            arrPos[i] = {nums[i], i};
        }
        
        // Sort the array by array element values
        sort(arrPos.begin(), arrPos.end());
        
        // To keep track of visited elements (initialize as false)
        vector<bool> visited(n, false);
        
        int swaps = 0;
        
        // Traverse the array elements
        for (int i = 0; i < n; i++) {
            // If already visited or already in the correct position
            if (visited[i] || arrPos[i].second == i) {
                continue;
            }
            
            // Find out the number of nodes in this cycle
            int cycle_size = 0;
            int j = i;
            
            while (!visited[j]) {
                visited[j] = true;
                
                // Move to the next node
                j = arrPos[j].second;
                cycle_size++;
            }
            
            // Update the number of swaps
            if (cycle_size > 1) {
                swaps += (cycle_size - 1);
            }
        }
        
        return swaps;
    }
};
```

### Time Complexity:
- **O(nlogn):** due to domination of sorting

### Space Complexity:
- **O(n):** to store the pairs

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>