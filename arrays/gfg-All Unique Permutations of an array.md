# [All Unique Permutations of an array](https://www.geeksforgeeks.org/problems/all-unique-permutations-of-an-array/0)

![](https://badgen.net/badge/Level/Medium/yellow)

Given an array arr[] of length n. Find all possible unique permutations of the array in sorted order. A sequence A is greater than sequence B if there is an index i for which Aj = Bj for all j<i and Ai > Bi.

### Approach Used :

-   To find all unique permutations of an array in sorted order, you can use backtracking along with sorting and a set to avoid duplicate permutations. The general approach is:
    -   Sort the array to ensure that the permutations are generated in lexicographic order.
    -   Use a backtracking function to generate the permutations.
    -   Use a set to avoid duplicates by checking if the permutation has been generated before.

### Code (C++)

```cpp
class Solution {
  public:
    vector<vector<int>> uniquePerms(vector<int> &arr, int n) {
        vector<vector<int>> result;
        vector<int> current;
        vector<bool> used(n, false);
        set<vector<int>> uniqueSet;

        sort(arr.begin(), arr.end());
        backtrack(arr, n, used, current, result, uniqueSet);
        return result;
    }

  private:
    void backtrack(vector<int> &arr, int n, vector<bool> &used, vector<int> &current, vector<vector<int>> &result, set<vector<int>> &uniqueSet) {
        if (current.size() == n) {
            if (uniqueSet.find(current) == uniqueSet.end()) {
                result.push_back(current);
                uniqueSet.insert(current);
            }
            return;
        }

        for (int i = 0; i < n; ++i) {
            if (used[i]) continue;

            // Skip duplicate elements
            if (i > 0 && arr[i] == arr[i - 1] && !used[i - 1]) continue;

            used[i] = true;
            current.push_back(arr[i]);
            backtrack(arr, n, used, current, result, uniqueSet);
            current.pop_back();
            used[i] = false;
        }
    }
};
```

### Time Complexity:
- **O(n⋅n!):** Sorting the array takes O(nlogn) time.In the worst case, where all elements are unique, there are n! permutations.The backtracking algorithm generates each permutation once. For each permutation, it takes O(n) time to add it to the result.

### Space Complexity:
- **O(n⋅n!):** the overall space complexity is dominated by the storage for permutations and the unique set.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>