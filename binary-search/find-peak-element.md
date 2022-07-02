# Find Peak Element

[https://leetcode.com/problems/find-peak-element/](https://leetcode.com/problems/find-peak-element/)

多个山峰找到任意一峰值即可

> A peak element is an element that is strictly greater than its neighbors.
>
> Given a **0-indexed** integer array `nums`, find a peak element, and return its index. If the array contains multiple peaks, return the index to **any of the peaks**.
>
> You may imagine that `nums[-1] = nums[n] = -∞`. In other words, an element is always considered to be strictly greater than a neighbor that is outside the array.
>
> You must write an algorithm that runs in `O(log n)` time.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: nums = [1,2,3,1]
> Output: 2
> Explanation: 3 is a peak element and your function should return the index number 2.
> ```
>
> **Example 2:**
>
> ```
> Input: nums = [1,2,1,3,5,6,4]
> Output: 5
> Explanation: Your function can return either index number 1 where the peak element is 2, or index number 5 where the peak element is 6.
> ```

{% hint style="info" %}
因为是找到任意一峰值 所谓峰值就是前后都比他小&#x20;
{% endhint %}

```
class Solution {
    public int findPeakElement(int[] nums) {
        int left = 0, right = nums.length - 1;
        while(left + 1 < right){
            int mid = (right - left) / 2 + left;
            if(nums[mid] < nums[mid + 1]){
                left = mid;
            }else if(nums[mid] < nums[mid - 1]){
                right = mid;
            }else{
                return mid;
            }
        }
        if(nums[left] < nums[right]) return right;
        return left;     
    }
}
```
