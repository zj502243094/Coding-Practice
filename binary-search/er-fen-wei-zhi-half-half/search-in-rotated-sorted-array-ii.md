# Search in Rotated Sorted Array II

[https://leetcode.com/problems/search-in-rotated-sorted-array-ii/](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/)

上一题follow up 有重复元素

```
class Solution {
    public boolean search(int[] nums, int target) {
        if(nums == null || nums.length == 0) return false;
        int left = 0, right = nums.length - 1;
        while(left + 1 < right){
            int mid = (right - left) / 2 + left;
            if(nums[mid] == target) return true;
            if(nums[mid] == nums[right]){
                right--;
            }else if(nums[mid] < nums[right]){
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
        if(nums[left] == target || nums[right] == target) return true;
        return false;
    }
}
```
