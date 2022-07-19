# Remove Duplicates from Sorted Array I / II

[https://leetcode.com/problems/remove-duplicates-from-sorted-array/](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

拍过序的数组 去掉重复数字 只重复1次

> Given an integer array `nums` sorted in **non-decreasing order**, remove the duplicates [**in-place**](https://en.wikipedia.org/wiki/In-place\_algorithm) such that each unique element appears only **once**. The **relative order** of the elements should be kept the **same**.
>
> Do **not** allocate extra space for another array. You must do this by **modifying the input array** [**in-place**](https://en.wikipedia.org/wiki/In-place\_algorithm) with O(1) extra memory.
>
> **Example 1:**
>
> ```
> Input: nums = [1,1,2]
> Output: 2, nums = [1,2,_]
> ```
>
>
>
> **Example 2:**
>
> ```
> Input: nums = [0,0,1,1,1,2,2,3,3,4]
> Output: 5, nums = [0,1,2,3,4,_,_,_,_,_]
> ```

```
class Solution {
    public int removeDuplicates(int[] nums) {
        if(nums == null || nums.length == 0) return 0;
        int i = 1;
        for(int j = 1; j < nums.length; j++){
            if(nums[j] != nums[i - 1]){
                nums[i++] = nums[j];
            }
        }
        return i;
    }
}
```

[https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/](https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/)\
拍过序的数组 去掉重复数字 最多不超过2次

> **Example 1:**
>
> ```
> Input: nums = [1,1,1,2,2,3]
> Output: 5, nums = [1,1,2,2,3,_]
> ```
>
> **Example 2:**
>
> ```
> Input: nums = [0,0,1,1,1,1,2,3,3]
> Output: 7, nums = [0,0,1,1,2,3,3,_,_]
> ```

```
class Solution {
    public int removeDuplicates(int[] A) {
        int i = 2;
        for (int j = 2; j < A.length; j++){
            if(A[j] != A[i - 2]){
                A[i++] = A[j];
            }
        }
        return i;
    }
}
```

拍过序的数组去掉重复数字 最多不超过k次

```
class Solution {
    public int removeDuplicates(int[] A) {
        int i = k;
        for (int j = k; j < A.length; j++){
            if(A[j] != A[i - k]){
                A[i++] = A[j];
            }
        }
        return i;
    }
}
```
