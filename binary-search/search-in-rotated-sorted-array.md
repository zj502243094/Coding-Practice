# Search in Rotated Sorted Array

[https://leetcode.com/problems/search-in-rotated-sorted-array/](https://leetcode.com/problems/search-in-rotated-sorted-array/)

在一个旋转过的排序数组找到目标值的位置

> There is an integer array `nums` sorted in ascending order (with **distinct** values).
>
> Prior to being passed to your function, `nums` is **possibly rotated** at an unknown pivot index `k` (`1 <= k < nums.length`) such that the resulting array is `[nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]]` (**0-indexed**). For example, `[0,1,2,4,5,6,7]` might be rotated at pivot index `3` and become `[4,5,6,7,0,1,2]`.
>
> Given the array `nums` **after** the possible rotation and an integer `target`, return _the index of_ `target` _if it is in_ `nums`_, or_ `-1` _if it is not in_ `nums`.
>
> You must write an algorithm with `O(log n)` runtime complexity.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: nums = [4,5,6,7,0,1,2], target = 0
> Output: 4
> ```
>
> **Example 2:**
>
> ```
> Input: nums = [4,5,6,7,0,1,2], target = 3
> Output: -1
> ```
>
> **Example 3:**
>
> ```
> Input: nums = [1], target = 0
> Output: -1
> ```

{% hint style="info" %}
需要判断 mid是在旋转位置之前还是之后去找target 用mid 和最前或者最后比较 并且端点和target比较
{% endhint %}

```
class Solution {
    public int search(int[] nums, int target) {
        if(nums == null || nums.length == 0) return -1;
        int left = 0, right = nums.length - 1;
        while(left + 1 < right){
            int mid = (right - left) / 2 + left;
            if(nums[mid] == target){
                return mid;
            }
            if(nums[mid] < nums[right]){
                if(nums[mid] < target && nums[right] >= target){
                    left = mid;
                }else{
                    right = mid;
                }
            }else{
                if(nums[mid] > target && nums[right] < target){
                    right = mid;
                }else{
                    left = mid;
                }
            }
        }
        if(nums[left] == target) return left;
        if(nums[right] == target) return right;
        return -1;
    }
}
```
