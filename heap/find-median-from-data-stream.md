# Find Median from Data Stream

[https://leetcode.com/problems/find-median-from-data-stream/](https://leetcode.com/problems/find-median-from-data-stream/)

> The **median** is the middle value in an ordered integer list. If the size of the list is even, there is no middle value and the median is the mean of the two middle values.
>
> * For example, for `arr = [2,3,4]`, the median is `3`.
> * For example, for `arr = [2,3]`, the median is `(2 + 3) / 2 = 2.5`.
>
> Implement the MedianFinder class:
>
> * `MedianFinder()` initializes the `MedianFinder` object.
> * `void addNum(int num)` adds the integer `num` from the data stream to the data structure.
> * `double findMedian()` returns the median of all elements so far. Answers within `10-5` of the actual answer will be accepted.

```
class MedianFinder {
    
    PriorityQueue<Integer> min;
    PriorityQueue<Integer> max;

    public MedianFinder() {
        min = new PriorityQueue();
        max = new PriorityQueue(Collections.reverseOrder());
    }
    
    public void addNum(int num) {
        max.offer(num);
        min.offer(max.poll());
        if (min.size() > max.size()) {
            max.offer(min.poll());
        }
    }
    
    public double findMedian() {
        if (max.size() != min.size()) {
            return max.peek();
        }
        return (max.peek() + min.peek()) / 2.0;
    }
}
```
