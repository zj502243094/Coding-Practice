# Window Sum

> Given an array of n integers, and a moving window(size k), move the window at each iteration from the start of the array, find the `sum` of the element inside the window at each moving.
>
> **样例**
>
> **Example 1**
>
> ```
> Input：array = [1,2,7,8,5], k = 3
> Output：[10,17,20]
> Explanation：
> 1 + 2 + 7 = 10
> 2 + 7 + 8 = 17
> 7 + 8 + 5 = 20
> ```

```
class Solution {
    public int[] findMaxAverage(int[] nums, int k) {
        int[] sums = new int[nums.length - k + 1];
        for(int i = 0; i < k; i++){
            sums[0] += nums[i];
        }
        for(int i = 1; i < sum.length; i++){
            sums[i] = sums[i - 1] - nums[i - 1] + nums[i + k - 1];
        }
        return sums;
    }
}
```
