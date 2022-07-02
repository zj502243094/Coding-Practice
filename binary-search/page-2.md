---
description: Lintcode
---

# First/Last Position of Target

First Position of Target: [https://www.lintcode.com/problem/14/](https://www.lintcode.com/problem/14/)

> Description
>
> Given a sorted array (ascending order) and a `target` number, find the first index of this number in $$O(log n)O(logn)$$ time complexity.
>
> If the `target` number does not exist in the array, return `-1`.
>
> **Example 1:**
>
> Input:
>
> ```
> tuple = [1,4,4,5,7,7,8,9,9,10]
> target = 1
> ```
>
> Output:
>
> ```
> 0
> ```
>
> Explanation:
>
> The first index of 1 is 0.
>
> **Example 2:**
>
> Input:
>
> ```
> tuple = [1, 2, 3, 3, 4, 5, 10]
> target = 3
> ```
>
> Output:
>
> ```
> 2
> ```
>
> Explanation:
>
> The first index of 3 is 2.

{% hint style="info" %}
因为我们需要找到第一个位置，所以当mid == target的时候 需要 right = mid
{% endhint %}

```
public class Solution {

    public int binarySearch(int[] nums, int target) {
        if(nums == null || nums.length == 0) return -1;
        int start = 0, end = nums.length - 1;
        while(start + 1 < end){
            int mid = (end - start) / 2 + start;
            if(nums[mid] < target){
                start = mid;
            } else {
                end = mid;
            }
        }
        if(nums[start] == target) return start;
        if(nums[end] == target) return end;
        return -1;
    }
}
```



Last Position of Target: [https://www.lintcode.com/problem/458](https://www.lintcode.com/problem/458)

> Find the last position of a `target` number in a sorted array. Return `-1` if target does not exist.
>
> Example
>
> **Example 1:**
>
> ```
> Input: nums = [1,2,2,4,5,5], target = 2
> Output: 2
> ```
>
> **Example 2:**
>
> ```
> Input: nums = [1,2,2,4,5,5], target = 6
> Output: -1
> ```

```
public class Solution {
    /**
     * @param nums: An integer array sorted in ascending order
     * @param target: An integer
     * @return: An integer
     */
    public int lastPosition(int[] nums, int target) {
        if(nums == null || nums.length == 0) return -1;
        int start = 0, end = nums.length - 1;
        while(start + 1 < end){
            int mid = (end - start) / 2 + start;
            if(nums[mid] > target){
                end = mid;
            } else {
                start = mid;
            }
        }
        if(nums[end] == target) return end;
        if(nums[start] == target) return start;
        return -1;
    }
}
```
