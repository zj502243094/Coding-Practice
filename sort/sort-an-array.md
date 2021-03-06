# Sort an Array

[https://leetcode.com/problems/sort-an-array/](https://leetcode.com/problems/sort-an-array/)\
\
数组排序

> Given an array of integers `nums`, sort the array in ascending order.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: nums = [5,2,3,1]
> Output: [1,2,3,5]
> ```
>
> **Example 2:**
>
> ```
> Input: nums = [5,1,1,2,0,0]
> Output: [0,0,1,1,2,5]
> ```

归并排序：time （nlog(n)） space(O(n))

```
class Solution {
    public int[] sortArray(int[] nums) {
        if(nums == null) return null;
        mergeSort(nums, 0, nums.length - 1);
        return nums;
    }
    private void mergeSort(int[] nums, int left, int right){
        if(left == right) return;
        int mid = (right - left) / 2 + left;
        mergeSort(nums, left, mid);
        mergeSort(nums, mid + 1, right);
        
        int[] tmp = new int[right - left + 1];
        int i = left, j = mid + 1;
        for(int k = 0; k < tmp.length; k++){
            if(i <= mid && (nums[i] <= nums[j] || j > right)){
                tmp[k] = nums[i++];
            }else{
                tmp[k] = nums[j++];
            }
        }
        for(int k = 0; k < tmp.length; k++){
            nums[left + k] = tmp[k];
        }
    }
}
```

快速排序  time  平均（nlog(n)）最坏（O（n^2）） space 平均（nlog(n)）最坏(O(n))

```
class Solution {
    public int[] sortArray(int[] nums) {
        if(nums == null || nums.length == 0) return null;
        quickSort(nums, 0, nums.length - 1);
        return nums;
    }
    private void quickSort(int[] nums, int left, int right){
        if(left >= right) return;
        
        int i = left, j = right;
        int pivot = nums[(right - left) / 2 + left];
        while(i <= j){
            while(i <= j && nums[i] < pivot){
                i++;
            }
            while(i <= j && nums[j] > pivot){
                j--;
            }
            if(i <= j){
                int t = nums[i];
                nums[i] = nums[j];
                nums[j] = t;
                i++;
                j--;
            }
        }
        quickSort(nums, left, j);
        quickSort(nums, i, right);
    }
}
```
