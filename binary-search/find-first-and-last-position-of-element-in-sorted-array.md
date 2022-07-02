# Find First And Last Position of Element in Sorted Array

[https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)

找到满足target区域的范围

> Given an array of integers `nums` sorted in non-decreasing order, find the starting and ending position of a given `target` value.
>
> If `target` is not found in the array, return `[-1, -1]`.
>
> You must write an algorithm with `O(log n)` runtime complexity.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: nums = [5,7,7,8,8,10], target = 8
> Output: [3,4]
> ```
>
> **Example 2:**
>
> ```
> Input: nums = [5,7,7,8,8,10], target = 6
> Output: [-1,-1]
> ```
>
> **Example 3:**
>
> ```
> Input: nums = [], target = 0
> Output: [-1,-1]
> ```

{% hint style="info" %}
做两次二分分别找到第一个和最后一个满足条件的元素左右端点就好
{% endhint %}

```
class Solution {
    public int[] searchRange(int[] nums, int target) {
        if(nums == null || nums.length == 0) return new int[]{-1, -1};
        int first = findFisrtPosition(nums, target);
        int second = findEndPosition(nums, target);
        return new int[]{first, second};
    }
    
    private int findFisrtPosition(int[] nums, int target){
        int left = 0, right = nums.length - 1;
        while(left + 1 < right){
            int mid = (right - left) / 2 + left;
            if(nums[mid] < target){
                left = mid;
            }else{
                right = mid;
            }
        }
        if(nums[left] == target) return left;
        if(nums[right] == target) return right;
        return -1;
    }
    
    private int findEndPosition(int[] nums, int target){
        int left = 0, right = nums.length - 1;
        while(left + 1 < right){
            int mid = (right - left) / 2 + left;
            if(nums[mid] > target){
                right = mid;
            }else{
                left = mid;
            }
        }
        if(nums[right] == target) return right;
        if(nums[left] == target) return left;
        return -1;
    }
}
```
