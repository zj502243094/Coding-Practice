# Sliding Window Median

[https://leetcode.com/problems/sliding-window-median/](https://leetcode.com/problems/sliding-window-median/)

> The **median** is the middle value in an ordered integer list. If the size of the list is even, there is no middle value. So the median is the mean of the two middle values.
>
> * For examples, if `arr = [2,3,4]`, the median is `3`.
> * For examples, if `arr = [1,2,3,4]`, the median is `(2 + 3) / 2 = 2.5`.

```
class Solution {
    
    PriorityQueue<Integer> min = new PriorityQueue<>();
    PriorityQueue<Integer> max = new PriorityQueue<>(Collections.reverseOrder());
    
    public double[] medianSlidingWindow(int[] nums, int k) {
        double[] res = new double[nums.length - k + 1];
        for (int i = 0; i < nums.length; i++) {
            add(nums[i]);
            if (i >= k - 1) {
                res[i - k + 1] = getMedian();
                remove(nums[i - k + 1]);
            }
        }
        return res;
    }
    private void add(int n) {
        max.add(n);
        min.add(max.poll());

        if (min.size() > max.size())
            max.add(min.poll());
    }
    private double getMedian() {
        if (min.size() == max.size()) 
            return ((double) min.peek() + (double) max.peek()) / 2;
        else
            return (double) max.peek();
    }
    private void remove(int n) {
        if (max.peek() >= n) 
            max.remove(n);
        else 
            min.remove(n);

        if (min.size() > max.size())
            max.add(min.poll());
        if (max.size() > min.size())
            min.add(max.poll());
    }
}
```

```
public List<Integer> medianSlidingWindow(int[] nums, int k) {
        // write your code here
        PriorityQueue<Integer> minHeap = new PriorityQueue<>();
        PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder());
        List<Integer> res = new ArrayList<>();
        for(int i = 0; i < nums.length; i++){
            if(maxHeap.size() <= minHeap.size()){
                minHeap.add(nums[i]);
                maxHeap.add(minHeap.poll());
            }else{
                maxHeap.add(nums[i]);
                minHeap.add(maxHeap.poll());
            }
            if(maxHeap.size() + minHeap.size() == k){
                if(maxHeap.size() >= minHeap.size()) {
                    res.add(maxHeap.peek());
                }
                else res.add(minHeap.peek());
                int st = i - k + 1;
                if(!maxHeap.remove(nums[i - k + 1])) minHeap.remove(nums[i - k + 1]);
            }
        }
        return res;
    }
```
