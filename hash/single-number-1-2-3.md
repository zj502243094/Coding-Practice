# Single Number 1 2 3

[https://leetcode.com/problems/single-number/](https://leetcode.com/problems/single-number/)

找到单一的数

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
记录每个数出现次数。 找到出现次数== 1的就行了
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
        for (int key : map.keySet()) {
            if (map.get(key) == 1) {
                res = key;
            }
        }
        return res;
    }
}
```

> Given an integer array `nums`, in which exactly two elements appear only once and all the other elements appear exactly twice. Find the two elements that appear only once. You can return the answer in **any order**.
>
> You must write an algorithm that runs in linear runtime complexity and uses only constant extra space.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: nums = [1,2,1,3,2,5]
> Output: [3,5]
> Explanation:  [5, 3] is also a valid answer.
> ```
>
> **Example 2:**
>
> ```
> Input: nums = [-1,0]
> Output: [-1,0]
> ```

```
class Solution {
    public int[] singleNumber(int[] nums) {
        int[] res = new int[2];
        if (nums == null || nums.length == 0) return null;
        Map<Integer, Integer> map = new HashMap();
        
        for (int i = 0; i < nums.length; i++) {
            map.put(nums[i], map.getOrDefault(nums[i], 0) + 1);
        }
        int i = 0;
        for (int key : map.keySet()) {
            if (map.get(key) == 1) {
                res[i++] = key;
            }
        }
        return res;
    }
}
```

```
class Solution {
    public int[] singleNumber(int[] nums) {
        List<Integer> res = new ArrayList<>();
        if (nums == null || nums.length == 0) return null;
        Map<Integer, Integer> map = new HashMap();
        
        for (int i = 0; i < nums.length; i++) {
            map.put(nums[i], map.getOrDefault(nums[i], 0) + 1);
        }
        for (int i : map.keySet()) {
            if (map.get(i) == 1) {
                res.add(i);
            }
        }
        int[] ans = new int[res.size()];
        for (int i = 0; i < res.size(); i++) {
            ans[i] = res.get(i);
        }
        return ans;
    }
}
```
