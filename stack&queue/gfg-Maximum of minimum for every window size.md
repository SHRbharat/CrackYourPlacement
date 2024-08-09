# [Maximum of minimum for every window size](https://www.geeksforgeeks.org/problems/maximum-of-minimum-for-every-window-size3453/1)

![](https://badgen.net/badge/Level/Hard/red)

Given an integer array. The task is to find the maximum of the minimum of every window size in the array.
Note: Window size varies from 1 to the size of the Array.

### Approach Used :

-   Left and Right Arrays:
    -   left[i] stores the index of the previous smaller element for arr[i].
    -   right[i] stores the index of the next smaller element for arr[i].
    -   These arrays help in determining the range for which arr[i] is the minimum element.
-   Calculate Maximum of Minimums:
    -   For each element arr[i], calculate the length of the window where arr[i] is the minimum.
    -   Update the result array at the index corresponding to this window length with the maximum value found for that window size.
-   Fill the Remaining Entries:
    -   After processing all elements, some entries in the result array might not be filled. The loop at the end ensures that if a maximum for a larger window size is less than a smaller one, the smaller window's value is propagated to the larger one.

### Code (C++)

```cpp
class Solution
{
public:
    vector<int> maxOfMin(int arr[], int n)
    {
        vector<int> result(n, 0);
        vector<int> left(n), right(n);

        // Initialize left and right for each element
        stack<int> s;

        // Fill elements of left[]
        for (int i = 0; i < n; i++)
        {
            while (!s.empty() && arr[s.top()] >= arr[i])
                s.pop();

            left[i] = s.empty() ? -1 : s.top();
            s.push(i);
        }

        // Clear the stack for next calculation
        while (!s.empty())
            s.pop();

        // Fill elements of right[]
        for (int i = n - 1; i >= 0; i--)
        {
            while (!s.empty() && arr[s.top()] >= arr[i])
                s.pop();

            right[i] = s.empty() ? n : s.top();
            s.push(i);
        }

        // Calculate max of min for every window size
        for (int i = 0; i < n; i++)
        {
            int length = right[i] - left[i] - 1;
            result[length - 1] = max(result[length - 1], arr[i]);
        }

        // Fill the remaining entries
        for (int i = n - 2; i >= 0; i--)
        {
            result[i] = max(result[i], result[i + 1]);
        }

        return result;
    }
};

```

### Time Complexity:
- **O(n):** The solution involves linear traversals of the array

### Space Complexity:
- **O(n):** The space complexity is linear due to the additional space required for the left, right, and result arrays, as well as the stack used for processing.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>