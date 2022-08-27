# Maximum Product Subarray

[https://leetcode.com/problems/maximum-product-subarray/](https://leetcode.com/problems/maximum-product-subarray/)

> Given an integer array `nums`, find a contiguous non-empty subarray within the array that has the largest product, and return _the product_.
>
> The test cases are generated so that the answer will fit in a **32-bit** integer.
>
> A **subarray** is a contiguous subsequence of the array.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: nums = [2,3,-2,4]
> <strong>Output: 6
> </strong><strong>Explanation:
> </strong> [2,3] has the largest product 6.</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: nums = [-2,0,-1]
> <strong>Output: 0
> </strong><strong>Explanation:
> </strong> The result cannot be 2, because [-2,-1] is not a subarray.</code></pre>

```
class Solution {
    public int maxProduct(int[] nums) {
        int n = nums.length;
        int res = nums[0];
        int pre = 0, sur = 0;
        for (int i = 0; i < n; i++) {
            pre = (pre == 0 ? 1 : pre) * nums[i];
            sur = (sur == 0 ? 1 : sur) * nums[n - 1 - i];
            res = Math.max(res, Math.max(pre, sur));
        }
        return res;
    }
}
```
