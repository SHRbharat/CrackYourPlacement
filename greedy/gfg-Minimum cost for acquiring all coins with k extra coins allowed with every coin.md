# [Minimum cost for acquiring all coins with k extra coins allowed with every coin](https://www.geeksforgeeks.org/minimum-cost-for-acquiring-all-coins-with-k-extra-coins-allowed-with-every-coin/)

![](https://badgen.net/badge/Level/Medium/yellow)

You are given a list of N coins of different denominations. You can pay an amount equivalent to any 1 coin and can acquire that coin. In addition, once you have paid for a coin, we can choose at most K more coins and can acquire those for free. The task is to find the minimum amount required to acquire all the N coins for a given value of K.
### Approach Used :

-   As per the question, we can see that at a cost of 1 coin, we can acquire at most K+1 coins. Therefore, in order to acquire all the n coins, we will be choosing ceil(n/(k+1)) coins and the cost of choosing coins will be minimum if we choose the smallest ceil(n/(k+1)) ( Greedy approach). The smallest ceil(n/(k+1)) coins can be found by simply sorting all the N values in increasing order. 

### Code (C++)

```cpp
int minCost(int coin[], int n, int k)  
{ 
    // sort the coins value 
    sort(coin, coin + n); 
  
    // calculate no. of coins needed 
    int coins_needed = ceil(1.0 * n /  (k + 1)); 
  
    // calculate sum of all selected coins 
    int ans = 0; 
    for (int i = 0; i <= coins_needed - 1;  i++)  
        ans += coin[i]; 
      
    return ans; 
}
```

### Time Complexity:
- **O(nlogn):** sorting

### Space Complexity:
- **O(1):** no extra space is used.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>