# Binary Search

每次将寻找的正确范围减半

Given a sorted integer array - nums, and an integer - Target

Find the any/first/last position of the target in nums

Return -1 if the target does not exist



[https://leetcode.com/problems/binary-search/](https://leetcode.com/problems/binary-search/)

> Given an array of integers `nums` which is sorted in ascending order, and an integer `target`, write a function to search `target` in `nums`. If `target` exists, then return its index. Otherwise, return `-1`.
>
> You must write an algorithm with `O(log n)` runtime complexity.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: nums = [-1,0,3,5,9,12], target = 9
> Output: 4
> Explanation: 9 exists in nums and its index is 4
> ```
>
> **Example 2:**
>
> ```
> Input: nums = [-1,0,3,5,9,12], target = 2
> Output: -1
> Explanation: 2 does not exist in nums so return -1
> ```

```
class Solution {
    public int search(int[] nums, int target) {
        if(nums == null || nums.length == 0) return -1;
        int s = 0, e = nums.length - 1;
        while(s + 1 < e){
            int m = (e - s) / 2 + s;
            if(nums[m] == target) {
                return m;
            }else if(nums[m] < target){
                s = m;
            }else{
                e = m;
            }
        }
        if(nums[s] == target) return s;
        if(nums[e] == target) return e;
        return -1;
    }
}
```
