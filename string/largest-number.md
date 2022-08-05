# Largest Number

[https://leetcode.com/problems/largest-number/](https://leetcode.com/problems/largest-number/)

> Given a list of non-negative integers `nums`, arrange them such that they form the largest number and return it.
>
> Since the result may be very large, so you need to return a string instead of an integer.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: nums = [10,2]
> <strong>Output: "210"</strong></code></pre>
>
> **Example 2:**
>
> <pre><code>Input: nums = [3,30,34,5,9]
> <strong>Output: "9534330"</strong></code></pre>

{% hint style="info" %}
数字最大放在前面 然后两数相加比较大小 降序排序

**nums**: \[3,30,34,5,9]   **after sort   (b+a) compareTo (a+b) strNums**: \["9","5","34","3","30"]
{% endhint %}

```
class Solution {
    public String largestNumber(int[] nums) {
        if (nums == null || nums.length == 0) return "";
        String[] strs = new String[nums.length];
        for (int i = 0; i < nums.length; i++) {
            strs[i] = Integer.toString(nums[i]);
        } 
        Arrays.sort(strs, (a, b) -> ((b + a).compareTo(a + b)));
        if (strs[0].equals("0")) return "0";
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < strs.length; i++) {
            sb.append(strs[i]);
        }
        return sb.toString();
    }
}
```
