# Single Number 1 2 3

[https://leetcode.com/problems/single-number/](https://leetcode.com/problems/single-number/)

> Given a **non-empty** array of integers `nums`, every element appears _twice_ except for one. Find that single one.
>
> You must implement a solution with a linear runtime complexity and use only constant extra space.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: nums = [2,2,1]
> Output: 1
> ```
>
> **Example 2:**
>
> ```
> Input: nums = [4,1,2,1,2]
> Output: 4
> ```

{% hint style="info" %}
记录每个数出现次数。
{% endhint %}

```
class Solution {
    public int singleNumber(int[] nums) {
        int res = -1;
        if (nums == null || nums.length == 0) return res;
        Map<Integer, Integer> map = new HashMap();
        
        for (int i = 0; i < nums.length; i++) {
            map.put(nums[i], map.getOrDefault(nums[i], 0) + 1);
        }
        for (int i : map.keySet()) {
            if (map.get(i) == 1) {
                res = i;
            }
        }
        return res;
    }
}
```
