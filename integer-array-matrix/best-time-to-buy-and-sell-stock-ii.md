# Best Time to Buy and Sell Stock II

[https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/)

每个股票 最多拿一天 可以当天买卖

> **Example 1:**
>
> <pre><code>Input: prices = [7,1,5,3,6,4]
> <strong>Output:7
> </strong><strong>Explanation:Buy on day 2 (price = 1) and sell on day 3 (price = 5), profit = 5-1 = 4.
> </strong>Then buy on day 4 (price = 3) and sell on day 5 (price = 6), profit = 6-3 = 3.
> Total profit is 4 + 3 = 7.</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: prices = [1,2,3,4,5]
> <strong>Output: 4
> </strong><strong>Explanation:Buy on day 1 (price = 1) and sell on day 5 (price = 5), profit = 5-1 = 4.
> </strong>Total profit is 4.</code></pre>

```
class Solution {
    public int maxProfit(int[] prices) {
        int res = 0;
        for (int i = 1; i < prices.length; i++) {
            if (prices[i] > prices[i - 1]) {
                res += prices[i] - prices[i - 1];
            }
        }
        return res;
    }
}
```
