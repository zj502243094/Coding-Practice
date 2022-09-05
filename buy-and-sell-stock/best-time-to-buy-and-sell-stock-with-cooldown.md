# Best Time to Buy and Sell Stock with Cooldown

[https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/)

有一天cooldown 不可以交易

> You are given an array `prices` where `prices[i]` is the price of a given stock on the `ith` day.
>
> Find the maximum profit you can achieve. You may complete as many transactions as you like (i.e., buy one and sell one share of the stock multiple times) with the following restrictions:
>
> * After you sell your stock, you cannot buy stock on the next day (i.e., cooldown one day).
>
> **Note:** You may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: prices = [1,2,3,0,2]
> <strong>Output:
> </strong> 3
> <strong>Explanation:
> </strong> transactions = [buy, sell, cooldown, buy, sell]</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: prices = [1]
> <strong>Output:
> </strong> 0</code></pre>

{% hint style="info" %}
```
buy[i] = Math.max(sell[i-2]-prices[i], buy[i-1])
prevSell = sell[i-1];
sell[i] = Math.max(buy[i]+prices[i], sell[i-1])
```
{% endhint %}

```
class Solution {
    public int maxProfit(int[] prices) {
        if (prices == null || prices.length < 2) return 0;
        int buy = -prices[0];
        int sell = 0;
        int prevSell = 0;
        for (int i = 1; i < prices.length; i++) {
            buy = Math.max(prevSell - prices[i], buy);
            prevSell = sell;
            sell = Math.max(buy + prices[i], sell);
        }
        return sell;
    }
}
```
