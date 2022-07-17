# Sort an Array

排序

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

归并排序：

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
