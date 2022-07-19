# Partition Array According to Given Pivot

[https://leetcode.com/problems/partition-array-according-to-given-pivot/](https://leetcode.com/problems/partition-array-according-to-given-pivot/)

小于pivot的前面 大于pivot的 后面 ==pivot 中间

> You are given a **0-indexed** integer array `nums` and an integer `pivot`. Rearrange `nums` such that the following conditions are satisfied:
>
> * Every element less than `pivot` appears **before** every element greater than `pivot`.
> * Every element equal to `pivot` appears **in between** the elements less than and greater than `pivot`.
> * The **relative order** of the elements less than `pivot` and the elements greater than `pivot` is maintained.

{% hint style="info" %}
扫一遍记录 \<pivot    ==pivot   >pivot 然后 填上。
{% endhint %}

```
class Solution {
    public int[] pivotArray(int[] nums, int pivot) {
        if(nums == null || nums.length == 0) return null;
        int[] res = new int[nums.length];
        
        int left = 0, right = nums.length - 1;
        int i = 0, count = 0;
        while(left <= right){
            if(nums[left] < pivot){
                res[i++] = nums[left];
            }else if(nums[left] == pivot){
                count++;
            }
            left++;
        }
        
        left = 0;
        for(int j = 0; j < count; j++){
            res[i++] = pivot;
        }
        while(left <= right){
            if(nums[left] > pivot){
                res[i++] = nums[left];
            }
            left++;
        }
        return res;
    }
}
```

```
class Solution {
    public int[] pivotArray(int[] nums, int pivot) {
        partition(nums, pivot);
        partition(nums, pivot + 1);
        return nums;
    }
    public void partition(int[] nums, int pivot) {
        if(nums == null || nums.length == 0) return;
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
    }
}
```

```
class Solution {
    public int[] pivotArray(int[] nums, int pivot) {
        if(nums == null || nums.length == 0) return null;
        
        int left = 0;
        int right = nums.length - 1;
        int i = 0;
        
        while(i <= right){
            if(nums[i] < pivot){
                swap(nums, left, i);
                left++;
                i++;
            }else if(nums[i] == pivot){
                i++;
            }else{
                swap(nums, right, i);
                right--;
            }
        }
        return nums;
    }
    private void swap(int[] nums, int i, int j){
        int t = nums[i];
        nums[i] = nums[j];
        nums[j] = t;
    }
}
```
