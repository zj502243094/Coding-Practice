# Move Zeroes

[https://leetcode.com/problems/move-zeroes/](https://leetcode.com/problems/move-zeroes/)

> Given an integer array `nums`, move all `0`'s to the end of it while maintaining the relative order of the non-zero elements.
>
> **Note** that you must do this in-place without making a copy of the array.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: nums = [0,1,0,3,12]
> Output: [1,3,12,0,0]
> ```
>
> **Example 2:**
>
> ```
> Input: nums = [0]
> Output: [0]
> ```

{% hint style="info" %}
定开始的位置 然后遍历数组 不是0 的就放前面
{% endhint %}

```
class Solution {
    public void moveZeroes(int[] nums) {
        if (nums == null || nums.length == 0) return;

        int j = 0;
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != 0) {
                int tmp = nums[i];
                nums[i] = nums[j];
                nums[j] = tmp;
                j++;
            }
        }
    }
}
```

{% hint style="info" %}
r 找到不为 0 的数 l 找到前面为 0 的数 交换
{% endhint %}

```
class Solution {
    public void moveZeroes(int[] nums) {
        if (nums == null || nums.length == 0) return;

        int l = 0, r = 0;
        while (r < nums.length) {
            while (r < nums.length && nums[r] == 0) {
                r++;
            }
            while (l < r && nums[l] != 0) {
                l++;
            }
            if (l < nums.length && r < nums.length) {
                int tmp = nums[r];
                nums[r] = nums[l];
                nums[l] = tmp;
                l++;
                r++;
            }
        }
    }
}
```
