# [Chocolate Distribution Problem](https://www.geeksforgeeks.org/problems/chocolate-distribution-problem3825/1)

![](https://badgen.net/badge/Level/Easy/green)

Given an array A[ ] of positive integers of size N, where each value represents the number of chocolates in a packet. Each packet can have a variable number of chocolates. There are M students, the task is to distribute chocolate packets among M students such that :
1. Each student gets exactly one packet.
2. The difference between maximum number of chocolates given to a student and minimum number of chocolates given to a student is minimum.

### Approach Used :

-   To solve this problem, we can use a greedy approach. The idea is to sort the array of chocolates, and then find the subarray of size M with the smallest difference between the maximum and minimum values.

### Code (C++)

```cpp
class Solution{
    public:
    long long findMinDiff(vector<long long> a, long long n, long long m){
        //code
        sort(a.begin(),a.end());
        
        long long min_diff = LLONG_MAX;
        
        for (long long i = 0; i + m - 1 < n; i++) {
            long long diff = a[i + m - 1] - a[i];
            if (diff < min_diff) 
                min_diff = diff;
        }
        
        return min_diff;
    }   
};
```

### Time Complexity:
- **O(nlogn):** sorting takes O(nlogn) then traversing the array takes O(n) time.

### Space Complexity:
- **O(1):** no extra space is used.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>