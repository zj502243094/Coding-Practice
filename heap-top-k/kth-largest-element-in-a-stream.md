# Kth Largest Element in a Stream

[https://leetcode.com/problems/kth-largest-element-in-a-stream/](https://leetcode.com/problems/kth-largest-element-in-a-stream/)

> Design a class to find the `kth` largest element in a stream. Note that it is the `kth` largest element in the sorted order, not the `kth` distinct element.
>
> Implement `KthLargest` class:
>
> * `KthLargest(int k, int[] nums)` Initializes the object with the integer `k` and the stream of integers `nums`.
> * `int add(int val)` Appends the integer `val` to the stream and returns the element representing the `kth` largest element in the stream.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input
> ["KthLargest", "add", "add", "add", "add", "add"]
> [[3, [4, 5, 8, 2]], [3], [5], [10], [9], [4]]
> <strong>Output : [null, 4, 5, 5, 8, 8]</strong></code></pre>

```
class KthLargest {
    PriorityQueue<Integer> pq;
    int k;
    public KthLargest(int k, int[] nums) {
        this.k = k;
        pq = new PriorityQueue<>();
        for (int num : nums) {
            add(num);
        }
    }
    
    public int add(int val) {
        pq.offer(val);
        if (pq.size() > k) {
            pq.poll();
        }
        return pq.peek();
    }
}
```
