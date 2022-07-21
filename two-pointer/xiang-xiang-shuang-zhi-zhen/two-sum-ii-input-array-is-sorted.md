# Two Sum II - Input Array Is Sorted

[https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)

排过序的array 两数和为target&#x20;

> **Example 1:**
>
> ```
> Input: numbers = [2,7,11,15], target = 9
> Output: [1,2]
> Explanation: The sum of 2 and 7 is 9. Therefore, index1 = 1, index2 = 2. We return [1, 2].
> ```
>
> **Example 2:**
>
> ```
> Input: numbers = [2,3,4], target = 6
> Output: [1,3]
> Explanation: The sum of 2 and 4 is 6. Therefore index1 = 1, index2 = 3. We return [1, 3].
> ```
>
> **Example 3:**
>
> ```
> Input: numbers = [-1,0], target = -1
> Output: [1,2]
> Explanation: The sum of -1 and 0 is -1. Therefore index1 = 1, index2 = 2. We return [1, 2].
> ```

```
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int[] res = new int[2];
        if(nums == null || nums.length == 0) return res;
        
        int l = 0, r = nums.length - 1;
        while(l < nums.length){
            if(nums[r] + nums[l] < target){
                l++;
            }else if(nums[r] + nums[l] > target){
                r--;
            }else{
                res[0] = l + 1;
                res[1] = r + 1;
                return res;
            }
        }
        return res;
    }
}
```
