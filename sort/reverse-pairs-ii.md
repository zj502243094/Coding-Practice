# Reverse Pairs II

[https://leetcode.com/problems/reverse-pairs/](https://leetcode.com/problems/reverse-pairs/)\
上面题FOLLOW UP nums\[i] > 2 \* nums\[j]

> Given an integer array `nums`, return _the number of **reverse pairs** in the array_.
>
> A reverse pair is a pair `(i, j)` where `0 <= i < j < nums.length` and `nums[i] > 2 * nums[j]`.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: nums = [1,3,2,3,1]
> Output: 2
> ```
>
> **Example 2:**
>
> ```
> Input: nums = [2,4,3,5,1]
> Output: 3
> ```

{% hint style="info" %}
第一问 是因为 排序 和比较是同一个逻辑 都是 num\[i] 和nums\[j] 直接比较\
第二问 merge 和 比较 是不同逻辑 nums\[i] > `2 * nums[j]`&#x20;
{% endhint %}

```
class Solution {
    public int reversePairs(int[] nums) {
        if(nums == null || nums.length == 0) return 0;
        int[] tmp = new int[nums.length];
        return mergeSort(nums, 0, nums.length - 1, tmp);
    }
    
    private int mergeSort(int[] nums, int left, int right, int[] tmp){
        if(left >= right) return 0;
        
        int mid = (right - left) / 2 + left;
        int res = 0;
        res += mergeSort(nums, left, mid, tmp);
        res += mergeSort(nums, mid + 1, right, tmp);
        res += merge(nums, left, mid, right, tmp);
        return res;
    }
    
    private int merge(int[] nums, int left, int mid, int right, int[] tmp){
        int i = left, t = left, k = 0, res = 0;
        for(int j = mid + 1; j <= right; j++) {
            while(t <= mid && nums[t] <= 2L * nums[j]) t++;
            res += mid - t + 1;
            while(i <= mid && nums[i] <= nums[j]) tmp[k++] = nums[i++];
            tmp[k++] = nums[j];
        }
        while(i <= mid) tmp[k++] = nums[i++];
        for(i = left; i <= right; i++) nums[i] = tmp[i - left];
        return res;
    }
}
```
