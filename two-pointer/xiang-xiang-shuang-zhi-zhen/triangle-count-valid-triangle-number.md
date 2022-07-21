# Triangle Count / Valid Triangle Number

[https://www.lintcode.com/problem/382/](https://www.lintcode.com/problem/382/)\
[https://leetcode.com/problems/valid-triangle-number/](https://leetcode.com/problems/valid-triangle-number/)

> Description
>
> Given an array of integers, how many three numbers can be found in the array, so that we can build an triangle whose three edges length is the three numbers that we find?
>
> ***
>
> *
>
> Example
>
> **Example 1:**
>
> ```
> Input: [3, 4, 6, 7]
> Output: 3
> Explanation:
> They are (3, 4, 6), 
>          (3, 6, 7),
>          (4, 6, 7)
> ```
>
> **Example 2:**
>
> ```
> Input: [4, 4, 4, 4]
> Output: 4
> Explanation:
> Any three numbers can form a triangle. 
> So the answer is C(3, 4) = 4
> ```

```
class Solution {
    public int triangleNumber(int[] nums) {
        int res = 0;
        if(nums == null || nums.length == 0) return res;
        Arrays.sort(nums);
        
        for(int i = 2; i < nums.length; i++){
            int target = nums[i];
            int l = 0, r = i - 1;
            while(l < r){
                if(nums[l] + nums[r] > target){
                    res += r - l;
                    r--;
                }else{
                    l++;
                }
            }
        }
        return res;
    }
}
```
