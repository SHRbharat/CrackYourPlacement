# [Smallest Positive Missing](https://www.geeksforgeeks.org/problems/smallest-positive-missing-number-1587115621/1)

![](https://badgen.net/badge/Level/Medium/yellow)

You are given an array arr[] of N integers. The task is to find the smallest positive number missing from the array.

### Approach Used :

-   The idea is to use the array itself to record the presence of numbers in the range [1, n].

-   *Segregate Positive Numbers:* First, segregate positive numbers from non-positive numbers. This step helps in ignoring the negative numbers and zeros, which are irrelevant for finding the smallest positive missing number.
-   *Mark Presence of Numbers:* Use the array elements as indices and mark the corresponding positions in the array to indicate the presence of numbers.
-   *Find the Missing Number:* Finally, iterate through the array to find the first index which is not marked, indicating the smallest missing positive number.

### Code (C++)

```cpp
class Solution
{
public:
    // Function to find the smallest positive number missing from the array.
    int missingNumber(int arr[], int n) 
    { 
        // Segregate positive and non-positive numbers
        int j = 0;
        for (int i = 0; i < n; ++i) {
            if (arr[i] <= 0) {
                swap(arr[i], arr[j]);
                ++j;
            }
        }

        // Now, arr[0..j-1] contains non-positive numbers and arr[j..n-1] contains all positive numbers
        // We only need to consider the positive part of the array

        // Mark presence of elements
        for (int i = j; i < n; ++i) {
            int num = abs(arr[i]);
            if (num <= n - j && arr[j + num - 1] > 0) {
                arr[j + num - 1] = -arr[j + num - 1];
            }
        }

        // Find the first missing positive number
        for (int i = 0; i < n - j; ++i) {
            if (arr[j + i] > 0) {
                return i + 1;
            }
        }

        // If all positions are marked, the missing number is n-j+1
        return n - j + 1;
    }
};

```

### Time Complexity:
- **O(n):** all loops will run n number of times in worst case.

### Space Complexity:
- **O(1):** no extra space is used.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>