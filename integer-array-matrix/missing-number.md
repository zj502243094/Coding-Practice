# Missing Number

[https://leetcode.com/problems/missing-number/](https://leetcode.com/problems/missing-number/)

> Given an array `nums` containing `n` distinct numbers in the range `[0, n]`, return _the only number in the range that is missing from the array._
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: nums = [3,0,1]
> <strong>Output:2
> </strong><strong>Explanation:n = 3 since there are 3 numbers, so all numbers are in the range [0,3]. 2 is the missing number in the range since it does not appear in nums.</strong></code></pre>
>
> **Example 2:**
>
> <pre><code>Input: nums = [0,1]
> <strong>Output:2
> </strong><strong>Explanation:n = 2 since there are 2 numbers, so all numbers are in the range [0,2]. 2 is the missing number in the range since it does not appear in nums.</strong></code></pre>
>
> **Example 3:**
>
> <pre><code>Input: nums = [9,6,4,2,3,5,7,0,1]
> <strong>Output:8</strong></code></pre>

{% hint style="info" %}
首先想到 将所有数  加到set里面 i <= n set 里面没出现过就是 res &#x20;

但是 space 是 extra O(n)
{% endhint %}

```
class Solution {
    public int missingNumber(int[] nums) {
        int n = nums.length;
        int res = -1;
        Set<Integer> set = new HashSet<>();
        for (int num : nums) {
            set.add(num);
        }
        for (int i = 0; i <= n; i++) {
            if (!set.contains(i)) {
                res = i;
            }
        }
        return res;
    }
}
```

{% hint style="info" %}
space : O(1)

新开一个sum 将 0 - n 之间所有的和 和 nums\[0 - n] 之前 差值为 res&#x20;
{% endhint %}

```
class Solution {
    public int missingNumber(int[] nums) {
        int n = nums.length;
        int sum = 0;
        for (int i = 0; i < n; i++) {
            sum += i;
            sum -= nums[i];
        }
        sum += n;
        return sum;
    }
}
```
