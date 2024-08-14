# [Tug of War](https://www.geeksforgeeks.org/tug-of-war/)

![](https://badgen.net/badge/Level/Hard/red)

Given a set of n integers, divide the set in two subsets of n/2 sizes each such that the absolute difference of the sum of two subsets is as minimum as possible. If n is even, then sizes of two subsets must be strictly n/2 and if n is odd, then size of one subset must be (n-1)/2 and size of other subset must be (n+1)/2.

### Approach Used :

-   Recursive Backtracking:
    -   The solution uses recursion to explore all possible subsets of the array.
    -   At each step, it either includes the current element in the subset or excludes it, then recursively continues to explore the possibilities.
-   Subset Sum Calculation:
    -   The goal is to find two subsets such that the absolute difference between their sums is minimized.
    -   The sum of all elements is computed, and each recursive call tries to form a subset of size n/2 that is as close as possible to half of the total sum.
-   Tracking the Best Solution:
    -   A boolean array soln keeps track of the current best solution (i.e., the subset with the minimum difference found so far).
    -   The minimum difference is stored in min_diff.

### Code (C++)

```cpp
#include <bits/stdc++.h> 
using namespace std; 
  
// function that tries every possible solution by calling itself recursively 
void TOWUtil(int* arr, int n, bool* curr_elements, int no_of_selected_elements, 
             bool* soln, int* min_diff, int sum, int curr_sum, int curr_position) 
{ 
    // checks whether the it is going out of bound 
    if (curr_position == n) 
        return; 
  
    // checks that the numbers of elements left are not less than the 
    // number of elements required to form the solution 
    if ((n/2 - no_of_selected_elements) > (n - curr_position)) 
        return; 
  
    // consider the cases when current element is not included in the solution 
    TOWUtil(arr, n, curr_elements, no_of_selected_elements, 
              soln, min_diff, sum, curr_sum, curr_position+1); 
  
    // add the current element to the solution 
    no_of_selected_elements++; 
    curr_sum = curr_sum + arr[curr_position]; 
    curr_elements[curr_position] = true; 
  
    // checks if a solution is formed 
    if (no_of_selected_elements == n/2) 
    { 
        // checks if the solution formed is better than the best solution so far 
        if (abs(sum/2 - curr_sum) < *min_diff) 
        { 
            *min_diff = abs(sum/2 - curr_sum); 
            for (int i = 0; i<n; i++) 
                soln[i] = curr_elements[i]; 
        } 
    } 
    else
    { 
        // consider the cases where current element is included in the solution 
        TOWUtil(arr, n, curr_elements, no_of_selected_elements, soln, 
                  min_diff, sum, curr_sum, curr_position+1); 
    } 
  
    // removes current element before returning to the caller of this function 
    curr_elements[curr_position] = false; 
} 
  
// main function that generate an arr 
void tugOfWar(int *arr, int n) 
{ 
    // the boolean array that contains the inclusion and exclusion of an element 
    // in current set. The number excluded automatically form the other set 
    bool* curr_elements = new bool[n]; 
  
    // The inclusion/exclusion array for final solution 
    bool* soln = new bool[n]; 
  
    int min_diff = INT_MAX; 
  
    int sum = 0; 
    for (int i=0; i<n; i++) 
    { 
        sum += arr[i]; 
        curr_elements[i] =  soln[i] = false; 
    } 
  
    // Find the solution using recursive function TOWUtil() 
    TOWUtil(arr, n, curr_elements, 0, soln, &min_diff, sum, 0, 0); 
  
    // Print the solution 
    cout << "The first subset is: "; 
    for (int i=0; i<n; i++) 
    { 
        if (soln[i] == true) 
            cout << arr[i] << " "; 
    } 
    cout << "\nThe second subset is: "; 
    for (int i=0; i<n; i++) 
    { 
        if (soln[i] == false) 
            cout << arr[i] << " "; 
    } 
} 
  
// Driver program to test above functions 
int main() 
{ 
    int arr[] = {23, 45, -34, 12, 0, 98, -99, 4, 189, -1, 4}; 
    int n = sizeof(arr)/sizeof(arr[0]); 
    tugOfWar(arr, n); 
    return 0; 
} 
```

### Time Complexity:
- **O(2^n):** where n is the size of the array. This is because every element can either be included or excluded from the subset.

### Space Complexity:
- **O(n):** due to the space used by the recursive call stack and the boolean arrays curr_elements and soln.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>