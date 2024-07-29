# [Find floor and ceil in an unsorted array](https://www.geeksforgeeks.org/find-floor-ceil-unsorted-array/)

![](https://badgen.net/badge/Level/Easy/green)

Given a sorted array and a value x, the ceiling of x is the smallest element in an array greater than or equal to x, and the floor is the greatest element smaller than or equal to x.

### Approach Used :

-   sorting the array and finding ceil and floor  lineraly will take O(nlogn) time.

-   To solve this in O(n), the idea is to traverse array and keep track of two distances with respect to x. 
    -   Minimum distance of element greater than or equal to x. 
    -   Minimum distance of element smaller than or equal to x.
    -   Finally print elements with minimum distances. 

### Code (C++)

```cpp
void floorAndCeil(int arr[], int n, int x)  
{  
    // Indexes of floor and ceiling  
    int fInd, cInd;  
  
    // Distances of current floor and ceiling  
    int fDist = INT_MAX, cDist = INT_MAX;  
  
    for (int i=0; i<n; i++)  
    {  
        // If current element is closer than  
        // previous ceiling.  
        if (arr[i] >= x && cDist > (arr[i] - x))  
        {  
        cInd = i;  
        cDist = arr[i] - x;  
        }  
  
        // If current element is closer than  
        // previous floor.  
        if (arr[i] <= x && fDist > (x - arr[i]))  
        {  
        fInd = i;  
        fDist = x - arr[i];  
        }  
    }  
  
    if (fDist == INT_MAX)  
    cout << "Floor doesn't exist " << endl;  
    else
    cout << "Floor is " << arr[fInd] << endl;  
  
    if (cDist == INT_MAX)  
    cout << "Ceil doesn't exist " << endl;  
    else
    cout << "Ceil is " << arr[cInd] << endl;  
}  
```

### Time Complexity:
- **O(n):** traverses the array once

### Space Complexity:
- **O(1):** no extra space is used.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>