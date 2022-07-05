# Peak Index in a Mountain Array

[https://leetcode.com/problems/peak-index-in-a-mountain-array/](https://leetcode.com/problems/peak-index-in-a-mountain-array/)

一座山峰找到峰值

> Let's call an array `arr` a **mountain** if the following properties hold:
>
> * `arr.length >= 3`
> * There exists some `i` with `0 < i < arr.length - 1` such that:
>   * `arr[0] < arr[1] < ... arr[i-1] < arr[i]`
>   * `arr[i] > arr[i+1] > ... > arr[arr.length - 1]`
>
> Given an integer array `arr` that is **guaranteed** to be a mountain, return any `i` such that `arr[0] < arr[1] < ... arr[i - 1] < arr[i] > arr[i + 1] > ... > arr[arr.length - 1]`.
>
> **Example 1:**
>
> ```
> Input: arr = [0,1,0]
> Output: 1
> ```
>
> **Example 2:**
>
> ```
> Input: arr = [0,2,1,0]
> Output: 1
> ```
>
> **Example 3:**
>
> ```
> Input: arr = [0,10,5,2]
> Output: 1
> ```

{% hint style="info" %}
只要峰值后一个位置比峰值还大 就还需要继续找直到 峰值+1位置比峰值小
{% endhint %}

```
class Solution {
    public int peakIndexInMountainArray(int[] arr) {
        if(arr == null || arr.length == 0) return -1;
        int left = 0, right = arr.length - 1;
        while(left + 1 < right){
            int mid = left + (right - left) / 2;
            if(arr[mid] > arr[mid + 1]){
                right = mid;
            }else{
                left = mid;
            }
        }
        if(arr[left] > arr[right]) return left;
        return right;
    }
}
```
