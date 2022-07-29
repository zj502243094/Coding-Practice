# Sliding Window Maximum

[https://leetcode.com/problems/sliding-window-maximum/](https://leetcode.com/problems/sliding-window-maximum/)

滑动窗口中最大值&#x20;

> You are given an array of integers `nums`, there is a sliding window of size `k` which is moving from the very left of the array to the very right. You can only see the `k` numbers in the window. Each time the sliding window moves right by one position.
>
> Return _the max sliding window_.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: nums = [1,3,-1,-3,5,3,6,7], k = 3
> Output: [3,3,5,5,6,7]
> Explanation: 
> Window position                Max
> ---------------               -----
> [1  3  -1] -3  5  3  6  7       3
>  1 [3  -1  -3] 5  3  6  7       3
>  1  3 [-1  -3  5] 3  6  7       5
>  1  3  -1 [-3  5  3] 6  7       5
>  1  3  -1  -3 [5  3  6] 7       6
>  1  3  -1  -3  5 [3  6  7]      7
> ```

{% hint style="info" %}
each element `nums[i]` in the array that we are about to insert

1. first check whether the leftmost index in the sliding window is out of bound
2. remove the rightmost indices if their corresponding elements are less than `nums[i]`
{% endhint %}

```
class Solution {
    public int[] maxSlidingWindow(int[] nums, int k) {
        int n = nums.length;
        if(n == 0 || k == 0) return new int[0];
        int[] res = new int[n - k + 1];
        Deque<Integer> dq = new ArrayDeque<>();
        
        for (int i = 0; i < n; i++) {
            while (!dq.isEmpty() && dq.peekFirst() <= i - k) {
                dq.pollFirst();
            }
            while (!dq.isEmpty() && nums[dq.peekLast()] < nums[i]) {
                dq.pollLast();
            }
            dq.offerLast(i);  // == dq.offer(i);
            if (i >= k - 1) {
                res[i - k + 1] = nums[dq.peekFirst()];
            }
        }
        return res;
    }
}
```

```
class Solution {
    public int[] maxSlidingWindow(int[] nums, int k) {
        int n = nums.length;
        if (n == 0 || k == 0) return new int[0];
        PriorityQueue<Integer> pq = new PriorityQueue<>(Collections.reverseOrder());
        int[] res = new int[n - k + 1];
        
        for (int i = 0; i < n; i++) {
            int start = i - k;
            if (start >= 0) {
                pq.remove(nums[start]);
            }
            pq.offer(nums[i]);
            if (pq.size() == k) {
                res[i - k + 1] = pq.peek();
            }
        }
        return res;
    }
}
```
