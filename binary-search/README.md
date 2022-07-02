# Binary Search

每次将寻找的正确范围减半

Given a sorted integer array - nums, and an integer - Target

Find the any/first/last position of the target in nums

Return -1 if the target does not exist



记忆点：

```
start + 1 < end                    //最后在while循环里只剩2个元素
mid = start + (end - start) / 2    // mid  end - start 是因为超出边界
nums[mid] == ,  <  , >   target 
nums[start] nums[end] ? target    
```

将原本 O(n) 的时间 变为 O(log(n))

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
        int start = 0;
        int end = nums.length - 1;
        while(start + 1 < end){
            int mid = (end - start) / 2 + start;
            if(nums[mid] == target){
                return mid;
            }else if(nums[mid] < target){
                start = mid;
            }else{
                end = mid;
            }
        }
        if(nums[start] == target){
            return start;
        }
        if(nums[end] == target){
            return end;
        }
        return -1;
    }
}
```
