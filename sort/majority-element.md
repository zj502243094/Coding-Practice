# Majority Element

[https://leetcode.com/problems/majority-element/](https://leetcode.com/problems/majority-element/)

> Given an array `nums` of size `n`, return _the majority element_.
>
> The majority element is the element that appears more than `⌊n / 2⌋` times. You may assume that the majority element always exists in the array.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: nums = [3,2,3]
> <strong>Output:
> </strong> 3</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: nums = [2,2,1,1,1,2,2]
> <strong>Output:
> </strong> 2</code></pre>

```
class Solution {
    public int majorityElement(int[] nums) {
        return divide(nums, 0, nums.length - 1);
    }
    private int divide(int[] nums, int left, int right) {
        if (left == right) return nums[left];
        int mid = (right - left) / 2 + left;
        int leftRes = divide(nums, left, mid);
        int rightRes = divide(nums, mid + 1, right);
        if (leftRes == rightRes) return leftRes;
        int leftCnt = conquer(nums, leftRes, left, right);
        int rightCnt = conquer(nums, rightRes, left, right);
        return leftCnt > rightCnt ? leftRes : rightRes;
    }
    private int conquer(int[] nums, int target, int left, int right) {
        int count = 0;
        for (int i = left; i <= right; i++) {
            if (nums[i] == target) count++;
        }
        return count;
    }
}
```

{% hint style="info" %}
投票法 遇到出现过的 + 1 没出现过的 -1&#x20;

直到最后剩下的就是majorityElement
{% endhint %}

```
class Solution {
    public int majorityElement(int[] nums) {
        int count = 0;
        int t = 0;
        for (int num : nums) {
            if (count == 0) t = num;
            count += (num == t) ? 1 : -1;
        }
        return t;
    }
}
```

```
class Solution {
    public int majorityElement(int[] nums) {
        Arrays.sort(nums);
        return nums[nums.length / 2];
    }
}
```
