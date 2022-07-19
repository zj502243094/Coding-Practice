# Partition Array I / II

[https://www.lintcode.com/problem/31/](https://www.lintcode.com/problem/31/)

> Description
>
> Given an array `nums` of integers and an int `k`, partition the array (i.e move the elements in "nums") such that:
>
> * All elements < _k_ are moved to the _left_
> * All elements >= _k_ are moved to the _right_
>
> Return the partitioning index, i.e the first index _i_ nums\[_i_] >= _k_.
>
> ***
>
> If all elements in `nums` are smaller than `k`, then return `nums.length`\
> $$0 <= nums.length <= 20000<=nums.length<=2000$$
>
> Example
>
> **Example 2:**
>
> Input:
>
> ```
> nums = [3,2,2,1]
> k = 2
> ```
>
> Output:
>
> ```
> 1
> ```
>
> Explanation:
>
> the real array is\[1,2,2,3].So return 1.
>
> Challenge
>
> Can you partition the array in-place and in O(n)

```
public class Solution {
    /**
     * @param nums: The integer array you should partition
     * @param k: An integer
     * @return: The index after partition
     */
    public int partitionArray(int[] nums, int pivot) {
        if(nums == null || nums.length == 0) return 0;
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
        return i;
    }
}
```

follow up 有边界 快排

> Partition an unsorted integer array into three parts:
>
> 1. The front part < _low_
> 2. The middle part >= _low_ & <= _high_
> 3. The tail part > _high_
>
> Return any of the possible solutions.
>
> low <= high in all testcases.
>
> **样例**
>
> Example 1:
>
> ```
> Input:
> [4,3,4,1,2,3,1,2]
> 2
> 3
> Output:
> [1,1,2,3,2,3,4,4]
> Explanation:
> [1,1,2,2,3,3,4,4] is also a correct answer, but [1,2,1,2,3,3,4,4] is not
> ```
>
> Example 2:
>
> ```
> Input:
> [3,2,1]
> 2
> 3
> Output:
> [1,2,3]
> ```

{% hint style="info" %}
我们建立首尾双指针`left`和`right`，`left`指示第一部分和第二部分的边界，`right`指示第二部分和第三部分的边界

* 第三个指针`mid`从`left`起向`right`移动，边扫描边实时更新两个边界。
  * 若 `nums[mid] > high` ： `right`指针左移。
  * 若 `nums[mid] < low` ：`left`和`mid`指针都向右移。
  * 若 `nums[mid]`在`low`和`high`之间 ：将指针`mid`右移。
{% endhint %}

```
public class Solution {
    /**
     * @param nums: an integer array
     * @param low: An integer
     * @param high: An integer
     * @return: nothing
     */
    public void partition2(int[] nums, int low, int high) {
        int left = 0, right = nums.length - 1;
        int mid = 0;
        
        while (mid <= right){
            if (nums[mid] > high){
                swap(nums, mid, right);
                right --;
            }
            else if (nums[mid] < low){
                swap(nums, mid, left);
                mid ++;
                left ++;
            }
            else{
                mid ++;
            }
        }
    }
    private void swap(int[] a, int i, int j) {
        int tmp = a[i];
        a[i] = a[j];
        a[j] = tmp;
    }
}
```
