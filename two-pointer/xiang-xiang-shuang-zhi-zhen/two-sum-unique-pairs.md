# Two Sum - Unique pairs

[https://www.lintcode.com/problem/587/](https://www.lintcode.com/problem/587/)

> Description
>
> Given an array of integers, find how many `unique pairs` in the array such that their sum is equal to a specific target number. Please return the number of pairs.
>
> ***
>
> Example
>
> **Example 1:**
>
> ```
> Input: nums = [1,1,2,45,46,46], target = 47 
> Output: 2
> Explanation:
>
> 1 + 46 = 47
> 2 + 45 = 47
> ```
>
> **Example 2:**
>
> ```
> Input: nums = [1,1], target = 2 
> Output: 1
> Explanation:
> 1 + 1 = 2
> ```

{% hint style="info" %}
当== target 时 res++; 并且 L++ 严重 L 和 L - 1 是否重复
{% endhint %}

```
public class Solution {
    /**
     * @param nums: an array of integer
     * @param target: An integer
     * @return: An integer
     */
    public int twoSum6(int[] nums, int target) {
        int res = 0;
        if(nums == null || nums.length == 0) return res;
        int l = 0, r = nums.length - 1;
        Arrays.sort(nums);

        while(l < r){
            if(nums[l] + nums[r] < target){
                l++;
            }else if(nums[l] + nums[r] == target){
                res++;
                l++;
                while(l < r && nums[l] == nums[l - 1]){
                    l++;
                }
            }else{
                r--;
            }
        }
        return res;
    }
}
```
