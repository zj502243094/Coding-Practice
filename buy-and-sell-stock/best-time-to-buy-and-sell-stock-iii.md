# Best Time to Buy and Sell Stock III

[https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iii/)

最多可以交易两次 找到最大收益

> You are given an array `prices` where `prices[i]` is the price of a given stock on the `ith` day.
>
> Find the maximum profit you can achieve. You may complete **at most two transactions**.
>
> **Note:** You may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: prices = [3,3,5,0,0,3,1,4]
> <strong>Output:
> </strong> 6
> <strong>Explanation:
> </strong> Buy on day 4 (price = 0) and sell on day 6 (price = 3), profit = 3-0 = 3.
> Then buy on day 7 (price = 1) and sell on day 8 (price = 4), profit = 4-1 = 3.</code></pre>

{% hint style="info" %}
buy1 找花最少的钱 sell1 最多的钱 - 最少的钱 buy2 是 再减去最少的钱&#x20;
{% endhint %}

```
class Solution {
    public int maxProfit(int[] prices) {
        if (prices == null || prices.length < 2) return 0;
        int buy1 = -prices[0];
        int sell1 = buy1 + prices[0];
        int buy2 = sell1 - prices[0];
        int sell2 = buy2 + prices[0];
        for (int i = 1; i < prices.length; i++) {
            buy1 = Math.max(buy1, -prices[i]);
            sell1 = Math.max(sell1, buy1 + prices[i]);
            buy2 = Math.max(buy2, sell1 - prices[i]);
            sell2 = Math.max(sell2, buy2 + prices[i]);
        }
        return Math.max(sell1, sell2);
    }
}
```
