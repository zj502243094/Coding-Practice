# Best Time to Buy and Sell Stock

[https://leetcode.com/problems/best-time-to-buy-and-sell-stock/](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

> You are given an array `prices` where `prices[i]` is the price of a given stock on the `ith` day.
>
> You want to maximize your profit by choosing a **single day** to buy one stock and choosing a **different day in the future** to sell that stock.
>
> Return _the maximum profit you can achieve from this transaction_. If you cannot achieve any profit, return `0`.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: prices = [7,1,5,3,6,4]
> <strong>Output: 5
> </strong><strong>Explanation:Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.</strong></code></pre>

```
class Solution {
    public int maxProfit(int[] prices) {
        int res = 0;
        int buy = Integer.MAX_VALUE;
        for (int price : prices) {
            buy = Math.min(buy, price);
            res = Math.max(price - buy, res);
        }
        return res;
    }   
}
```

{% hint style="success" %}
[https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/discuss/1569081/Java-Simple-and-Clean-DP-solutions-for-all-6-Buy-and-Sell-Stock-questions-on-LeetCode](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/discuss/1569081/Java-Simple-and-Clean-DP-solutions-for-all-6-Buy-and-Sell-Stock-questions-on-LeetCode)
{% endhint %}
