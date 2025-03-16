# Frequency of the Most Frequent Element

[https://leetcode.com/problems/frequency-of-the-most-frequent-element/](https://leetcode.com/problems/frequency-of-the-most-frequent-element/)

总共最多操作K次 后 使nums有最高出现次数出现 求出现操作后的最高次数&#x20;

> You are given an integer array `nums` and an integer `k`. In one operation, you can choose an index of `nums` and increment the element at that index by `1`.
>
> Return _the **maximum possible frequency** of an element after performing **at most**_ `k` _operations_.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: nums = [1,2,4], k = 5
> <strong>Output:3
> </strong>Explanation: Increment the first element three times and the second element two times to make nums = [4,4,4].
> 4 has a frequency of 3.
> </code></pre>
>
> **Example 2:**
>
> <pre><code>Input: nums = [1,4,8,13], k = 5
> <strong>Output:2
> </strong><strong>Explanation:There are multiple optimal solutions:
> </strong>- Increment the first element three times to make nums = [4,4,8,13]. 4 has a frequency of 2.
> - Increment the second element four times to make nums = [1,8,8,13]. 8 has a frequency of 2.
> - Increment the third element five times to make nums = [1,4,13,13]. 13 has a frequency of 2.
> </code></pre>

{% hint style="info" %}
sliding window 题目        数组排序后&#x20;

在nums\[l, r] 需要 k 次变得和nums\[r]相同  sum\[i, j] + k 和nums\[r] \* (r - l + 1)
{% endhint %}

```
class Solution {
    public int maxFrequency(int[] nums, int k) {
        int res = 0;
        if (nums == null || nums.length == 0) return res;
        Arrays.sort(nums);
        
        long sum = 0;
        int l = 0, r = 0;
        while (r < nums.length) {
            sum += nums[r];
            if (sum + k < 1L * nums[r] * (r - l + 1)) {
                sum -= nums[l];
                l++;
            }
            res = Math.max(res, r - l + 1);
            r++;
        }
        return res;
    }
}
```
