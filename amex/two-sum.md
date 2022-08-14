# Two Sum

[https://leetcode.com/problems/two-sum/](https://leetcode.com/problems/two-sum/)

> Given an array of integers `nums` and an integer `target`, return _indices of the two numbers such that they add up to `target`_.
>
> You may assume that each input would have _**exactly**_** one solution**, and you may not use the _same_ element twice.
>
> You can return the answer in any order.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: nums = [2,7,11,15], target = 9
> Output: [0,1]
> Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
> ```

{% hint style="info" %}
建一个 map 存 数字 和 其位置
{% endhint %}

```
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int[] res = new int[2];
        Map<Integer, Integer> map = new HashMap();
        for(int i = 0; i < nums.length; i++) {
            if(map.containsKey(target - nums[i])){
                res[0] = map.get(target - nums[i]);
                res[1] = i;
            } else {
                map.put(nums[i], i);
            }
        }
        return res;
    }
}
```
