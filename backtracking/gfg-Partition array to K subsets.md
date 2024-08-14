# [Partition array to K subsets](https://www.geeksforgeeks.org/problems/partition-array-to-k-subsets/1)

![](https://badgen.net/badge/Level/Hard/red)

Given an integer array a[ ] of N elements and an integer K, the task is to check if the array a[ ] could be divided into K non-empty subsets with equal sum of elements.
Note: All elements of this array should be part of exactly one partition.

### Approach Used :

-   Check Feasibility:
    -   If the sum of the array elements (totalSum) is not divisible by K, it's impossible to partition the array into K subsets with equal sum.
-   Calculate Target Sum:
    -   Each subset must have a sum equal to totalSum / K.
-   Use Backtracking:
    -   Use a recursive function to try to assign each element of the array to one of the K subsets.
    -   Keep track of the current sum of each subset.
    -   Use an array visited to ensure each element is only considered once.
-   Base Case:
    -   If all K subsets are successfully filled with the target sum, return true.
-   Recursive Case:
    -   For each element, try adding it to any subset that doesn't exceed the target sum.
    -   Recursively check if adding the current element allows for a valid partition.

### Code (C++)

```cpp
class Solution {
public:
    bool isKPartitionPossible(int a[], int n, int k) {
        int totalSum = 0;
        for (int i = 0; i < n; i++) {
            totalSum += a[i];
        }
        
        // If total sum is not divisible by k, partitioning is not possible
        if (totalSum % k != 0) {
            return false;
        }
        
        int targetSum = totalSum / k;
        vector<bool> visited(n, false);
        return canPartition(0, a, visited, k, 0, targetSum, n);
    }

private:
    bool canPartition(int index, int a[], vector<bool>& visited, int k, int currentSum, int targetSum, int n) {
        // If we have successfully created k-1 subsets with the target sum, the last one must also have the target sum
        if (k == 1) {
            return true;
        }
        
        // If current sum equals target sum, move on to the next subset
        if (currentSum == targetSum) {
            return canPartition(0, a, visited, k - 1, 0, targetSum, n);
        }
        
        // Try to assign the current element to a subset
        for (int i = index; i < n; i++) {
            if (!visited[i] && currentSum + a[i] <= targetSum) {
                visited[i] = true;
                if (canPartition(i + 1, a, visited, k, currentSum + a[i], targetSum, n)) {
                    return true;
                }
                visited[i] = false; // backtrack
            }
        }
        
        return false;
    }
};

```

### Time Complexity:
- **O(2^n):**  where n is the number of elements in the array. This is due to the recursive exploration of subsets.

### Space Complexity:
- **O(n):** which is used by the visited array and the recursion stack.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>