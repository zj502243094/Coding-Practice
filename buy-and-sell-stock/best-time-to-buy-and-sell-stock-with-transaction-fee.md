# Best Time to Buy and Sell Stock with Transaction Fee

[https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-transaction-fee/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-transaction-fee/)

可以无限次交易 但是每次有手续费

> You are given an array `prices` where `prices[i]` is the price of a given stock on the `ith` day, and an integer `fee` representing a transaction fee.
>
> Find the maximum profit you can achieve. You may complete as many transactions as you like, but you need to pay the transaction fee for each transaction.
>
> **Note:** You may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: prices = [1,3,2,8,4,9], fee = 2
> <strong>Output:
> </strong> 8
> <strong>Explanation:
> </strong> The maximum profit can be achieved by:
> - Buying at prices[0] = 1
> - Selling at prices[3] = 8
> - Buying at prices[4] = 4
> - Selling at prices[5] = 9
> The total profit is ((8 - 1) - 2) + ((9 - 4) - 2) = 8.</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: prices = [1,3,7,5,10,3], fee = 3
> <strong>Output: 6</strong></code></pre>

{% hint style="info" %}
```java
buy[i] = Math.max(sell[i - 1] - prices[i], buy[i - 1])
sell[i] = Math.max(buy[i] + prices[i] - fee, sell[i - 1])
```
{% endhint %}

```
class Solution {
    public int maxProfit(int[] prices, int fee) {
        if (prices == null || prices.length < 2) return 0;
        int buy = -prices[0];
        int sell = 0;
        for (int i = 1; i < prices.length; i++) {
            sell = Math.max(buy + prices[i] - fee, sell);
            buy = Math.max(sell - prices[i], buy);
        }
        return sell;
    }
}
```
