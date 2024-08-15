# [Check if reversing a sub array make the array sorted](https://www.geeksforgeeks.org/check-reversing-sub-array-make-array-sorted/)

![](https://badgen.net/badge/Level/Medium/yellow)

Given an array of n distinct integers. The task is to check whether reversing any one sub-array can make the array sorted or not. If the array is already sorted or can be made sorted by reversing any one subarray, print “Yes“, else print “No“.

### Approach Used :

-   Method 1: Brute force (O(n3))
Consider every subarray and check if reversing the subarray makes the whole array sorted. If yes, return True. If reversing any of the subarrays doesn’t make the array sorted, then return False. Considering every subarray will take O(n2), and for each subarray, checking whether the whole array will get sorted after reversing the subarray in consideration will take O(n). Thus overall complexity would be O(n3).

-   Method 2: Sorting ( O(n*log(n) )) 
The idea is to compare the given array with its sorted version. Make a copy of the given array and sort it. Now, find the first index and last index in the given array which does not match with the sorted array. If no such indices are found (given array was already sorted), return True. Else check if the elements between the found indices are in decreasing order, if Yes then return True else return False



### Code (C++)

```cpp
bool checkReverse(int arr[], int n) 
{ 
    // Copying the array. 
    int temp[n]; 
    for (int i = 0; i < n; i++) 
        temp[i] = arr[i]; 
  
    // Sort the copied array. 
    sort(temp, temp + n); 
  
    // Finding the first mismatch. 
    int front; 
    for (front = 0; front < n; front++) 
        if (temp[front] != arr[front]) 
            break; 
  
    // Finding the last mismatch. 
    int back; 
    for (back = n - 1; back >= 0; back--) 
        if (temp[back] != arr[back]) 
            break; 
  
    // If whole array is sorted 
    if (front >= back) 
        return true; 
  
    // Checking subarray is decreasing or not. 
    do
    { 
        front++; 
        if (arr[front - 1] < arr[front]) 
            return false; 
    } while (front != back); 
  
    return true; 
} 
```

### Time Complexity:
- **O(n*log(n)):** sorting

### Space Complexity:
- **O(n):** space for sorted array

### Approach Used-2 (linear Time sorting):

-   The idea to solve this problem is based on the observation that if we perform one rotation of any subarray in the sorted array (increasing order), then we there will be exactly one subarray which will be in decreasing order. So, we have to find that rotated subarray and perform one rotation on it. Finally check if the array becomes sorted or not.

-   Initialize two variables x and y with -1.
-   Iterate over the array.
    -   Find the first number for which a[i] > a[i+1] and store it into x. 
    -   Similarly, Store index i+1 as well into y, As this will keep track of the ending of the subarray which is needed to reverse.
-   Check if x == -1 then array is already sorted so return true.
-   Otherwise, reverse the array from index x to index y.
    -   Traverse the array to check for every element is sorted or not.
        -   If not sorted, return false.
-   Finally, return true.

### Code (C++)

```cpp
bool sortArr(int a[], int n) 
{ 
    int x = -1; 
    int y = -1; 
  
    for (int i = 0; i < n - 1; i++) { 
        if (a[i] > a[i + 1]) { 
            if (x == -1) { 
                x = i; 
            } 
            y = i + 1; 
        } 
    } 
  
    if (x != -1) { 
        reverse(a + x, a + y + 1); 
        for (int i = 0; i < n - 1; i++) { 
            if (a[i] > a[i + 1]) { 
                return false; 
                return 0; 
            } 
        } 
    } 
  
    return true; 
} 
```

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>