# Contains Duplicate 1 2 3

[https://leetcode.com/problems/contains-duplicate/](https://leetcode.com/problems/contains-duplicate/)

一个数组 是否有 重复

> Given an integer array `nums`, return `true` if any value appears **at least twice** in the array, and return `false` if every element is distinct.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: nums = [1,2,3,1]
> Output: true
> ```
>
> **Example 2:**
>
> ```
> Input: nums = [1,2,3,4]
> Output: false
> ```
>
> **Example 3:**
>
> ```
> Input: nums = [1,1,1,3,3,4,3,2,4,2]
> Output: true
> ```

```
class Solution {
    public boolean containsDuplicate(int[] nums) {
        Set<Integer> set = new HashSet<>();
        for (int i : nums) set.add(i);
        if (nums.length != set.size()) return true;
        return false;
    }
}


class Solution {
    public boolean containsDuplicate(int[] nums) {
        Set<Integer> set = new HashSet<>();
        for (int i : nums) {
            if (!set.add(i)) return true;
        }
        return false;
    }
}
```





[https://leetcode.com/problems/contains-duplicate-ii/](https://leetcode.com/problems/contains-duplicate-ii/)

一个数组 是否有距离小于K的重复数

> Given an integer array `nums` and an integer `k`, return `true` if there are two **distinct indices** `i` and `j` in the array such that `nums[i] == nums[j]` and `abs(i - j) <= k`.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: nums = [1,2,3,1], k = 3
> Output: true
> ```
>
> **Example 2:**
>
> ```
> Input: nums = [1,0,1,1], k = 1
> Output: true
> ```
>
> **Example 3:**
>
> ```
> Input: nums = [1,2,3,1,2,3], k = 2
> Output: false
> ```

```
class Solution {
    public boolean containsNearbyDuplicate(int[] nums, int k) {
        Set<Integer> set = new HashSet<>();
        for (int i = 0; i < nums.length; i++) {
            if (set.contains(nums[i])) return true;
            set.add(nums[i]);
            if (set.size() > k) set.remove(nums[i - k]);
        }
        return false;
    }
}
```





[https://leetcode.com/problems/contains-duplicate-iii/](https://leetcode.com/problems/contains-duplicate-iii/)

数组中两个距离小于K的数 差值小于T&#x20;

> Given an integer array `nums` and two integers `k` and `t`, return `true` if there are **two distinct indices** `i` and `j` in the array such that `abs(nums[i] - nums[j]) <= t` and `abs(i - j) <= k`.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: nums = [1,2,3,1], k = 3, t = 0
> Output: true
> ```
>
> **Example 2:**
>
> ```
> Input: nums = [1,0,1,1], k = 1, t = 2
> Output: true
> ```
>
> **Example 3:**
>
> ```
> Input: nums = [1,5,9,1,5,9], k = 2, t = 3
> Output: false
> ```

{% hint style="info" %}
加入到一个TreeSet 中&#x20;

ceil >= 当前数的最小数

floor <= 当前数的最大数
{% endhint %}

```
class Sution {
    public boolean containsNearbyAlmostDuplicate(int[] nums, int k, int t) {
        TreeSet<Integer> set = new TreeSet<>();
        for (int i = 0; i < nums.length; i++) {
            Integer ceil = set.ceiling(nums[i]);
            Integer floor = set.floor(nums[i]);
            if (ceil != null && ceil - nums[i] <= t) return true;
            if (floor != null && nums[i] - floor <= t) return true;
            set.add(nums[i]);
            if (set.size() > k) set.remove(nums[i - k]);
        }
        return false;
    }
}
```
