# Sort Colors

[https://leetcode.com/problems/sort-colors/](https://leetcode.com/problems/sort-colors/)

> Given an array `nums` with `n` objects colored red, white, or blue, sort them [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm) so that objects of the same color are adjacent, with the colors in the order red, white, and blue.
>
> We will use the integers `0`, `1`, and `2` to represent the color red, white, and blue, respectively.
>
> You must solve this problem without using the library's sort function.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: nums = [2,0,2,1,1,0]
> Output: [0,0,1,1,2,2]
> ```
>
> **Example 2:**
>
> ```
> Input: nums = [2,0,1]
> Output: [0,1,2]
> ```

{% hint style="info" %}
1. 先将 1 作为 pivot 然后 再讲 2  作为 pivot\
   &#x20;![](<../.gitbook/assets/image (5) (2).png>)

2\. 扫一遍记录 有几个0 几个1 几个2 然后 填上。
{% endhint %}

```
class Solution {
    public void sortColors(int[] nums) {
        partition(nums, 1);
        partition(nums, 2);
    }
    
    public void partition(int[] nums, int pivot) {
        if(nums == null || nums.length == 0) return;
        int i = 0, j = nums.length - 1;
        while(i <= j){
            while(i <= j && nums[i] < pivot){
                i++;
            }
            while(i <= j && nums[j] >= pivot){
                j--;
            }
            if(i <= j){
                int t = nums[i];
                nums[i++] = nums[j];
                nums[j--] = t;
            }
        }
    }
}
```

{% hint style="info" %}
left&#x20;
{% endhint %}

```
class Solution {
    public void sortColors(int[] nums) {
        if(nums == null || nums.length == 0) return;
        
        int left = 0;
        int right = nums.length - 1;
        int i = 0;
        
        while(i <= right){
            if(nums[i] == 0){
                swap(nums, left, i);
                left++;
                i++;
            }else if(nums[i] == 1){
                i++;
            }else{
                swap(nums, right, i);
                right--;
            }
        }
    }
    private void swap(int[] nums, int i, int j){
        int t = nums[i];
        nums[i] = nums[j];
        nums[j] = t;
    }
}
```
