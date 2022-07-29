# Longest Consecutive Sequence

[https://leetcode.com/problems/longest-consecutive-sequence/](https://leetcode.com/problems/longest-consecutive-sequence/)

> Given an unsorted array of integers `nums`, return _the length of the longest consecutive elements sequence._
>
> You must write an algorithm that runs in `O(n)` time.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: nums = [100,4,200,1,3,2]
> Output: 4
> Explanation: The longest consecutive elements sequence is [1, 2, 3, 4]. Therefore its length is 4.
> ```
>
> **Example 2:**
>
> ```
> Input: nums = [0,3,7,2,5,8,4,6,0,1]
> Output: 9
> ```

{% hint style="info" %}
最长连续数 找到当前数 +1 -1 然后 看长度
{% endhint %}

```
class Solution {
    public int longestConsecutive(int[] nums) {
        int res = 0;
        if (nums == null || nums.length == 0) return res;
        Set<Integer> set = new HashSet<>();
        for (int num : nums) set.add(num);
        
        for (int num : nums) {
            if (set.contains(num)) {
                set.remove(num);
                int l = num - 1;
                int r = num + 1;
                while (set.contains(l)) {
                    set.remove(l);
                    l--;
                }
                while (set.contains(r)) {
                    set.remove(r);
                    r++;
                }
                res = Math.max(res, r - l - 1);
            }
        }
        return res;
    }
}
```
