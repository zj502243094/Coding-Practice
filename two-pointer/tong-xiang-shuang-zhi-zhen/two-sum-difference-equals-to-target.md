# Two Sum - Difference equals to target

排序过的数组差 为target

> Description
>
> Given an sorted array of integers, find two numbers that their `difference` equals to a target value.\
> Return a list with two number like `[num1, num2]` that the difference of `num1` and `num2` equals to target value, and `num1` is less than `num2`.
>
> It's guaranteed there is only one available solution.\
> Note: Requires O(1) space complexity to comple
>
> Example
>
> Example 1:
>
> ```
> Input: nums = [2, 7, 15, 24], target = 5 
> Output: [2, 7] 
> Explanation:
> (7 - 2 = 5)
> ```
>
> Example 2:
>
> ```
> Input: nums = [1, 1], target = 0
> Output: [1, 1] 
> Explanation:
> (1 - 1 = 0)
> ```

{% hint style="info" %}
num[j](https://www.jiuzhang.com/solution/two-sum-difference-equals-to-target/)-num[i](https://www.jiuzhang.com/solution/two-sum-difference-equals-to-target/)< target   太小 j++;

numj - numi > target 太大 i++;

numj - numi == target 返回答案 \
当 i == j时，j++，保证num\[j]>num\[i]
{% endhint %}

```
public class Solution {
    /**
     * @param nums: an array of Integer
     * @param target: an integer
     * @return: [num1, num2] (index1 < index2)
     */
    public int[] twoSum7(int[] nums, int target) {
        int[] res = new int[2];
        if(nums == null || nums.length == 0) return res;
        target = Math.abs(target);
        
        int l = 0, r = 1;
        while(r < nums.length){
            if(nums[r] - nums[l] < target){
                r++;
            }else if(nums[r] - nums[l] > target){
                l++;
            }else{
                res[0] = nums[l];
                res[1] = nums[r];
                return res;
            }
            if(l == r) {
                r++;
            }
        }
        return res;
    }
}
```

```
class Pair {
    public int idx, num;
    public Pair(int i, int n){
        this.idx = i;
        this.num = n;
    }
}

public class Solution {
    public int[] twoSum7(int[] nums, int target) {
        int[] ans = new int[2];
        if(nums == null || nums.length == 0) return ans;
        target = Math.abs(target);

        Pair[] pairs = new Pair[nums.length];
        for(int i = 0; i < nums.length; i++){
            pairs[i] = new Pair(i, nums[i]);
        }
        Arrays.sort(pairs, (p1, p2) -> Integer.compare(p1.num, p2.num));

        for(int l = 0, r = 1; r < nums.length; r++){
            while(l < r && pairs[r].num - pairs[l].num > target){
                l++;
            }
            if(l != r && pairs[r].num - pairs[l].num == target){
                ans[0] = pairs[l].num;
                ans[1] = pairs[r].num;
                return ans;
            }
        }
        return ans;
    }
}
```
