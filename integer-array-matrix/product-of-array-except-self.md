# Product of Array Except Self

[https://leetcode.com/problems/product-of-array-except-self/](https://leetcode.com/problems/product-of-array-except-self/)

> Given an integer array `nums`, return _an array_ `answer` _such that_ `answer[i]` _is equal to the product of all the elements of_ `nums` _except_ `nums[i]`.
>
> The product of any prefix or suffix of `nums` is **guaranteed** to fit in a **32-bit** integer.
>
> You must write an algorithm that runs in `O(n)` time and without using the division operation.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: nums = [1,2,3,4]
> <strong>Output: [24,12,8,6]</strong></code></pre>
>
> **Example 2:**
>
> <pre><code>Input: nums = [-1,1,0,-3,3]
> <strong>Output: [0,0,9,0,0]</strong></code></pre>

{% hint style="info" %}
前缀乘积
{% endhint %}

```
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int n = nums.length;
        int[] res = new int[n];
        
        int[] left = new int[n];
        left[0] = 1;
        for (int i = 1; i < n; i++) {
            left[i] = left[i - 1] * nums[i - 1];
        }
        int[] right = new int[n];
        right[n - 1] = 1;
        for (int i = n - 2; i >= 0; i--) {
            right[i] = right[i + 1] * nums[i + 1];
        }
        for (int i = 0; i < n; i++) {
            res[i] = left[i] * right[i];
        }
        return res;
    }
}
```
