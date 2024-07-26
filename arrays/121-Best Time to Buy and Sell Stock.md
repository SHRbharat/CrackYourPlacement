# [121. Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

![](https://badgen.net/badge/Level/Easy/green)

You are given an array prices where prices[i] is the price of a given stock on the ith day.

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.

### Approach Used :

-   The approach iterates through the list of prices, keeping track of the minimum price encountered so far (buyItem) and calculating the potential profit at each step by subtracting the minimum price from the current price. If this potential profit exceeds the previously recorded maximum profit (profit), it updates the maximum profit accordingly, and ultimately returns this value.

### Code (C++)

```cpp
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int buyItem = prices[0];
        int profit = 0;
        for(int i = 1; i< prices.size(); i++){
            if(buyItem > prices[i]){
                buyItem = prices[i];
            } else if(prices[i] - buyItem > profit){
                profit = prices[i] - buyItem;
            }
        }
        return profit;
    }
};
```

### Time Complexity:
- **O(n):** iterates through the array once

### Space Complexity:
- **O(1):** doesn't creates any extra space.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>