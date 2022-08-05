# Kth Largest Element in an Array

[https://leetcode.com/problems/kth-largest-element-in-an-array/](https://leetcode.com/problems/kth-largest-element-in-an-array/)

> Given an integer array `nums` and an integer `k`, return _the_ `kth` _largest element in the array_.
>
> Note that it is the `kth` largest element in the sorted order, not the `kth` distinct element.
>
> You must solve it in `O(n)` time complexity.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: nums = [3,2,1,5,6,4], k = 2
> <strong>Output: 5</strong></code></pre>
>
> **Example 2:**
>
> <pre><code>Input: nums = [3,2,3,1,2,4,5,5,6], k = 4
> <strong>Output: 4</strong></code></pre>

{% hint style="info" %}
最大堆
{% endhint %}

```
class Solution {
    public int findKthLargest(int[] nums, int k) {
        int res = 0;
        PriorityQueue<Integer> pq = new PriorityQueue<>(Collections.reverseOrder());
        for (int num : nums) {
            pq.offer(num);
        }
        for (int i = 0; i < k; i++) {
            res = pq.poll();
        }
        return res;
    }
}
```

{% hint style="info" %}
最小堆
{% endhint %}

```
class Solution {
    public int findKthLargest(int[] nums, int k) {
        int res = 0;
        PriorityQueue<Integer> pq = new PriorityQueue<>();
        
        for (int num : nums) {
            pq.offer(num);
            if (pq.size() > k) {
                pq.poll();
            }
            res = pq.peek();
        }
        return res;
    }
}
```
