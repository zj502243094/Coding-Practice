# Recover Rotated Sorted Array

[https://www.lintcode.com/problem/39/](https://www.lintcode.com/problem/39/)

> Description
>
> Given a **rotated** sorted array, return it to sorted array in-place.（Ascending）
>
> What is rotated array?
>
> * For example, the orginal array is \[1,2,3,4], The rotated array of it can be \[1,2,3,4], \[2,3,4,1], \[3,4,1,2], \[4,1,2,3]
>
> Example
>
> **Example 1:**
>
> Input:
>
> ```
> array = [4,5,1,2,3]
> ```
>
> Output:
>
> ```
> [1,2,3,4,5]
> ```
>
> Explanation:
>
> Restore the rotated sorted array.
>
> **Example 2:**
>
> Input:
>
> ```
> array = [6,8,9,1,2]
> ```
>
> Output:
>
> ```
> [1,2,6,8,9]
> ```

{% hint style="info" %}
\[4,5,1,2,3] 找到 1 位置 前面 翻转 \[5, 4] 后面翻转\[3, 2, 1] 再全部翻转
{% endhint %}

```
public class Solution {
    /**
     * @param nums: An integer array
     * @return: nothing
     */
    public void recoverRotatedSortedArray(List<Integer> nums) {
        for(int i = 0; i < nums.size() - 1; i++){
            if(nums.get(i) > nums.get(i + 1)){
                reverse(nums, 0, i);
                reverse(nums, i + 1, nums.size() - 1);
                reverse(nums, 0, nums.size() - 1);
            }
        }
    }
    private void reverse(List<Integer> nums, int start, int end){
        int i = start, j = end;
        while(i < j){
            int t = nums.get(i);
            nums.set(i, nums.get(j));
            nums.set(j, t);
            i++;
            j--;
        }
    }
}
```
