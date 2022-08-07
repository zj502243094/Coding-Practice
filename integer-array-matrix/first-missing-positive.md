# First Missing Positive

[https://leetcode.com/problems/first-missing-positive/](https://leetcode.com/problems/first-missing-positive/)

> Given an unsorted integer array `nums`, return the smallest missing positive integer.
>
> You must implement an algorithm that runs in `O(n)` time and uses constant extra space.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: nums = [1,2,0]
> <strong>Output:3</strong></code></pre>
>
> **Example 2:**
>
> <pre><code>Input: nums = [3,4,-1,1]
> <strong>Output:2</strong></code></pre>
>
> **Example 3:**
>
> <pre><code>Input: nums = [7,8,9,11,12]
> <strong>Output:1</strong></code></pre>

{% hint style="info" %}
排序 一遍 如果 小于 1 继续 如果大于 1 res++ 找到第一个  > res 的&#x20;

**T/S:** O(n lg n)/O(1)
{% endhint %}

```
class Solution {
    public int firstMissingPositive(int[] nums) {
        Arrays.sort(nums);
        int res = 1;
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] < 1) continue;
            else {
                if (nums[i] == res) res++;
                else if (nums[i] > res) return res;
            }
        }
        return res;
    }
}
```

{% hint style="info" %}
**T/S:** O(n)/O(n)
{% endhint %}

```
class Solution {
    public int firstMissingPositive(int[] nums) {
        int max = Integer.MIN_VALUE;
        Set<Integer> set = new HashSet();
        for (int num : nums) {
            set.add(num);
            max = Math.max(max, num);
        }
        if (max < 1) max = 1;
        for (int i = 1; i <= max; i++) {
            if (!set.contains(i)) {
                return i;
            }
        }
        return max + 1;
    }
}
```

{% hint style="info" %}
**T/S:** O(n)/O(1)
{% endhint %}

```
class Solution {
    public int firstMissingPositive(int[] nums) {
        int n = nums.length;
        for (int i = 0; i < n; i++) {
            while (nums[i] >= 1 && nums[i] <= n && nums[i] != nums[nums[i] - 1]) {
                swap(nums, i, nums[i] - 1);
            }
        }
        for (int i = 0; i < n; i++) {
            if (nums[i] != i + 1) {
                return i + 1;
            }
        }
        return n + 1;
    }
    private void swap(int[] nums, int i, int j) {
	    int temp = nums[i];
	    nums[i] = nums[j];
	    nums[j] = temp;
    }
}
```

[https://leetcode.com/problems/first-missing-positive/discuss/1318705/Java-or-1-ms-time-beats-96-or-3-progressive-methods-with-Idea](https://leetcode.com/problems/first-missing-positive/discuss/1318705/Java-or-1-ms-time-beats-96-or-3-progressive-methods-with-Idea)
