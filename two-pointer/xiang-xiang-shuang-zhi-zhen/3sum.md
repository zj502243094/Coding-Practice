# 3Sum

[https://leetcode.com/problems/3sum/](https://leetcode.com/problems/3sum/)\
三数和为0

> Given an integer array nums, return all the triplets `[nums[i], nums[j], nums[k]]` such that `i != j`, `i != k`, and `j != k`, and `nums[i] + nums[j] + nums[k] == 0`.
>
> Notice that the solution set must not contain duplicate triplets.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: nums = [-1,0,1,2,-1,-4]
> Output: [[-1,-1,2],[-1,0,1]]
> ```

{% hint style="info" %}
设定nums\[i] 为 -target 然后就是 剩下两数和为target unique pairs
{% endhint %}

```
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        List<List<Integer>> res = new ArrayList<>();
        if(nums == null || nums.length == 0) return res;
        Arrays.sort(nums);
        
        for(int i = 0; i < nums.length - 2; i++){
            if(i > 0 && nums[i] == nums[i - 1]){
                continue;
            }
            int target = - nums[i];
            int l = i + 1, r = nums.length - 1;
            
            while(l < r){
                if(nums[l] + nums[r] < target){
                    l++;
                }else if(nums[l] + nums[r] > target){
                    r--;
                }else{
                    List<Integer> item = new ArrayList<>();
                    item.add(nums[i]);
                    item.add(nums[l]);
                    item.add(nums[r]);
                    res.add(item);
                    l++;
                    while(l < r && nums[l] == nums[l - 1]){
                        l++;
                    }
                }
            }
        }
        return res;
    }
}
```
