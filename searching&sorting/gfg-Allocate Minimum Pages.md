# [Allocate Minimum Pages](https://www.geeksforgeeks.org/problems/allocate-minimum-number-of-pages0937/1)

![](https://badgen.net/badge/Level/Medium/yellow)

You have n books, each with arr[i] a number of pages. m students need to be allocated contiguous books, with each student getting at least one book.
Out of all the permutations, the goal is to find the permutation where the sum of the maximum number of pages in a book allotted to a student should be the minimum, out of all possible permutations.

Note: Return -1 if a valid assignment is not possible, and allotment should be in contiguous order (see the explanation for better understanding).

### Approach Used :

-   Binary Search on Result:
    -   We need to determine the minimum possible value of the maximum pages a student can read.
    -   The lowest possible maximum would be the maximum pages of a single book (since each student needs at least one book).
    -   The highest possible maximum would be the sum of all pages (if only one student reads all the books).
-   Greedy Allocation:
    -   For a mid-point value during binary search, check if it’s possible to allocate books to all students such that no student reads more than this mid-point number of pages.
    -   If it’s possible, search for a smaller possible value (to minimize further).
    -   If not, search for a larger possible value (since the current value is too small).
-   Greedy Function:
    -   Iterate through the array and allocate books to students while keeping the sum of pages allocated to each student within the mid-point value.
    -   If you need more students than m to keep the allocations within this limit, then it means the mid-point value is too small.

### Code (C++)

```cpp
class Solution {
public:
    bool isPossible(int arr[], int n, int m, long long mid) {
        int studentCount = 1;
        long long pagesSum = 0;

        for (int i = 0; i < n; i++) {
            if (arr[i] > mid) return false; // Single book has more pages than mid

            if (pagesSum + arr[i] > mid) {
                studentCount++;
                pagesSum = arr[i];
                
                if (studentCount > m) return false; // Need more students than available
            } else {
                pagesSum += arr[i];
            }
        }
        return true;
    }

    long long findPages(int n, int arr[], int m) {
        if (m > n) return -1; // More students than books

        long long low = *max_element(arr, arr + n); // Max single book page count
        long long high = accumulate(arr, arr + n, 0LL); // Sum of all pages
        long long result = -1;

        while (low <= high) {
            long long mid = (low + high) / 2;

            if (isPossible(arr, n, m, mid)) {
                result = mid; // Store the current possible result
                high = mid - 1; // Try for a smaller maximum
            } else {
                low = mid + 1; // Increase the maximum
            }
        }

        return result;
    }
};

```

### Time Complexity:
- **O(n * log(sum of all pages)):** isPossible takes O(n) time and binary search runs in O(log(sum(arr))).

### Space Complexity:
- **O(1):** no extra space is used.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>