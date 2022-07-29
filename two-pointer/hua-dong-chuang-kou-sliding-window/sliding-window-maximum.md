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
