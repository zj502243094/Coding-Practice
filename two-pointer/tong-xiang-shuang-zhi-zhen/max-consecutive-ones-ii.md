# Max Consecutive Ones II

[https://leetcode.com/problems/max-consecutive-ones-ii/](https://leetcode.com/problems/max-consecutive-ones-ii/)

翻转 其中 一个 0 为 1。最长为 1 的连续数组是多长

> Given a binary array `nums`, return _the maximum number of consecutive_ `1`_'s in the array if you can flip at most one_ `0`.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: nums = [1,0,1,1,0]
> Output: 4
> Explanation: Flip the first zero will get the maximum number of consecutive 1s. After flipping, the maximum number of consecutive 1s is 4.
> ```
>
> **Example 2:**
>
> ```
> Input: nums = [1,0,1,1,0,1]
> Output: 4
> ```

{% hint style="info" %}
每次遇到 1 cur++ 遇到1后第一个0 last = cur + 1 （前次最长连续1 + 翻转一个0 ）

用last + cur 进行最后的比较
{% endhint %}

```
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int res = 0;
        if (nums == null || nums.length == 0) return res;
        
        int curCount = 0;
        int lastCount = 0;
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] == 1) {
                curCount++;
            } else {
                lastCount = curCount + 1;
                curCount = 0;
            }
            res = Math.max(res, lastCount + curCount);
        }
        return res;
    }
}
```

{% hint style="info" %}
右指针 记录0的个数 保证结果长度里面 最多有 1 个 0

当0的个数大于1时 zero=2 左指针移动 直到 zero = 1 为最长长度
{% endhint %}

```
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int res = 0;
        if (nums == null || nums.length == 0) {
            return res;
        }
        
        int l = 0, r = 0;
        int zero = 0;
        while (r < nums.length) {
            if (nums[r] == 0) {
                zero++;
            }
            r++;
            if (zero > 1) {
                if (nums[l] == 0) {
                    zero--;
                }
                l++;
            }
            res = Math.max(res, r - l);
        }
        return res;
    }
}
```
