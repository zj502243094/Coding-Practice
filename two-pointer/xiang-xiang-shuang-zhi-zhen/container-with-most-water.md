# Container With Most Water

[https://leetcode.com/problems/container-with-most-water/description/](https://leetcode.com/problems/container-with-most-water/description/)

> You are given an integer array `height` of length `n`. There are `n` vertical lines drawn such that the two endpoints of the `ith` line are `(i, 0)` and `(i, height[i])`.
>
> Find two lines that together with the x-axis form a container, such that the container contains the most water.
>
> Return _the maximum amount of water a container can store_.
>
> **Notice** that you may not slant the container.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://s3-lc-upload.s3.amazonaws.com/uploads/2018/07/17/question_11.jpg)
>
> <pre><code><strong>Input: height = [1,8,6,2,5,4,8,3,7]
> </strong><strong>Output: 49
> </strong><strong>Explanation: The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.
> </strong></code></pre>
>
> **Example 2:**
>
> <pre><code><strong>Input: height = [1,1]
> </strong><strong>Output: 1
> </strong></code></pre>

{% hint style="info" %}
暴力解法 是 O n 方。 但是用 two pointer 每次谁小动谁 O(n)
{% endhint %}

```
class Solution {
    public int maxArea(int[] height) {
        int len = height.length;
        int l = 0;
        int r = len - 1;
        int max = Math.min(height[l], height[r]) * (r - l);
        while (l < r) {
            if (height[l] <= height[r]) {
                l++;
            } else {
                r--;
            }
            max = Math.max(max, Math.min(height[l], height[r]) * (r - l));
        }
        return max;
    }
}
```
