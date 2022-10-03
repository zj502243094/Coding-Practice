# Split Array Largest Sum

[https://leetcode.com/problems/split-array-largest-sum/](https://leetcode.com/problems/split-array-largest-sum/)

将nums分成M份 每份和最小

> Given an array `nums` which consists of non-negative integers and an integer `m`, you can split the array into `m` non-empty continuous subarrays.
>
> Write an algorithm to minimize the largest sum among these `m` subarrays.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: nums = [7,2,5,10,8], m = 2
> <strong>Output: 18
> </strong><strong>Explanation:
> </strong>There are four ways to split nums into two subarrays.
> The best way is to split it into [7,2,5] and [10,8],
> where the largest sum among the two subarrays is only 18.</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: nums = [1,2,3,4,5], m = 2
> <strong>Output: 9</strong></code></pre>
>
> **Example 3:**
>
> <pre><code>Input: nums = [1,4,4], m = 3
> <strong>Output: 4</strong></code></pre>

{% hint style="info" %}
getCnt  是满足小于subArraySum的个数
{% endhint %}

```
class Solution {
    public int splitArray(int[] nums, int m) {
        int max = 0;
        long sum = 0;
        for (int num : nums) {
            max = Math.max(num, max);
            sum += num;
        }
        if (m == 1) return (int)sum;
        long left = max;
        long right = sum;
        while (left + 1 < right) {
            long mid = (right - left) / 2 + left;
            if (getCnt(nums, mid) <= m) {
                right = mid;
            } else {
                left = mid;
            }
        }
        if (getCnt(nums, left) <= m) return (int)left;
        return (int)right;
    }
    private int getCnt(int[] nums, long subArraySum) {
        int count = 1;
        long sum = 0;
        for (int num : nums) {
            sum += num;
            if (sum > subArraySum) {
                sum = num;
                count++;
            }
        }
        return count;
    } 
}
```
