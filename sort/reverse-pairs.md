# Reverse Pairs

前面数比 后面数大为 逆序对\
[https://www.lintcode.com/problem/532/](https://www.lintcode.com/problem/532/)

> Two numbers in the array, if the previous number is greater than the following number, then the two numbers form a reverse order pair. Give you an array, find out the total number of reverse order pairs in this array.\
> Summary: if a \[i] > a \[j] and i < j, a \[i] and a \[j] form a reverse order pair.
>
> Example
>
> **Example1**
>
> ```
> Input:  A = [2, 4, 1, 3, 5]
> Output: 3
> Explanation:
> (2, 1), (4, 1), (4, 3) are reverse pairs
> ```
>
> **Example2**
>
> ```
> Input:  A = [1, 2, 3, 4]
> Output: 0
> Explanation:
> No reverse pair
> ```

{% hint style="info" %}
排序后左右相比 当 nums\[i] > nums\[j] 并且 i < mid   res += mid - i + 1;
{% endhint %}

```
public int reversePairs(int[] nums) {
        if(nums == null || nums.length == 0) return 0;
        int[] tmp = new int[nums.length];
        return mergeSort(nums, 0, nums.length - 1, tmp);
    }
    
    private int mergeSort(int[] nums, int left, int right, int[] tmp){
        if(left == right) return 0;
        int mid = (right - left) / 2 + left;
        int res = 0;
        res += mergeSort(nums, left, mid, tmp);
        res += mergeSort(nums, mid + 1, right, tmp);
        
        int i = left, j = mid + 1;
        for(int k = 0; k < right - left + 1; k++){
            if(i <= mid && (j > right || nums[i] <= nums[j])){
                tmp[k] = nums[i++];
            }else{
                tmp[k] = nums[j++];
                if(i <= mid){
                    res += mid - i + 1;
                }
            }
        }
        for(int k = 0; k < right - left + 1; k++){
            nums[left + k] = tmp[k];
        }
        return res;
    }
```
