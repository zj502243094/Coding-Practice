---
description: Partition Array According to Given Pivot
---

# Partition Array

[https://www.lintcode.com/problem/31/](https://www.lintcode.com/problem/31/)

> Description
>
> Given an array `nums` of integers and an int `k`, partition the array (i.e move the elements in "nums") such that:
>
> * All elements < _k_ are moved to the _left_
> * All elements >= _k_ are moved to the _right_
>
> Return the partitioning index, i.e the first index _i_ nums\[_i_] >= _k_.
>
> ***
>
> If all elements in `nums` are smaller than `k`, then return `nums.length`\
> $$0 <= nums.length <= 20000<=nums.length<=2000$$
>
> Example
>
> **Example 2:**
>
> Input:
>
> ```
> nums = [3,2,2,1]
> k = 2
> ```
>
> Output:
>
> ```
> 1
> ```
>
> Explanation:
>
> the real array is\[1,2,2,3].So return 1.
>
> Challenge
>
> Can you partition the array in-place and in O(n)

```
public class Solution {
    /**
     * @param nums: The integer array you should partition
     * @param k: An integer
     * @return: The index after partition
     */
    public int partitionArray(int[] nums, int pivot) {
        if(nums == null || nums.length == 0) return 0;
        int i = 0, j = nums.length - 1;
        while(i <= j){
            while(i <= j && nums[i] < pivot){
                i++;
            }
            while(i <= j && nums[j] >= pivot){
                j--;
            }
            if(i <= j){
                int t = nums[i];
                nums[i++] = nums[j];
                nums[j--] = t;
            }
        }
        return i;
    }
}
```
