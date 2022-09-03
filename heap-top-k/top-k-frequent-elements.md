# Top K Frequent Elements

[https://leetcode.com/problems/top-k-frequent-elements/](https://leetcode.com/problems/top-k-frequent-elements/)

> Given an integer array `nums` and an integer `k`, return _the_ `k` _most frequent elements_. You may return the answer in **any order**.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: nums = [1,1,1,2,2,3], k = 2
> <strong>Output: [1,2]</strong></code></pre>
>
> **Example 2:**
>
> <pre><code>Input: nums = [1], k = 1
> <strong>Output: [1]</strong></code></pre>

```
class Solution {
    public int[] topKFrequent(int[] nums, int k) {
        int[] res = new int[k];
        if (nums == null || nums.length == 0) return res;
        Map<Integer, Integer> map = new HashMap();
        for (int num : nums) {
            map.put(num, map.getOrDefault(num, 0) + 1);
        }
        
        PriorityQueue<Integer> pq = new PriorityQueue((a, b) -> map.get(a) - map.get(b));  
        for (int key : map.keySet()) {
            pq.offer(key);
            if (pq.size() > k) {
                pq.poll();
            }
        }
        for (int i = 0; i < k; i++) {
            res[i] = pq.poll();
        }
        return res;
    }
}
```

```
class Solution {
    public int[] topKFrequent(int[] nums, int k) {
        int[] res = new int[k];
        if (nums == null || nums.length == 0) return res;
        Map<Integer, Integer> map = new HashMap();
        for (int num : nums) {
            map.put(num, map.getOrDefault(num, 0) + 1);
        }
        
        PriorityQueue<Integer> pq = new PriorityQueue((a, b) -> map.get(b) - map.get(a));  
        for (int key : map.keySet()) {
            pq.offer(key);
        }
        for (int i = 0; i < k; i++) {
            res[i] = pq.poll();
        }
        return res;
    }
}
```
