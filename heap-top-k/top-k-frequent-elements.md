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

{% hint style="info" %}
minHeap  (Olog(k))
{% endhint %}

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

{% hint style="info" %}
maxHeap (Olog(n))
{% endhint %}

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

{% hint style="info" %}
bucket sort   O(n)
{% endhint %}

```
class Solution {
    public int[] topKFrequent(int[] nums, int k) {
        List<Integer>[] bucket = new List[nums.length + 1];
        Map<Integer, Integer> map = new HashMap<>();
        for (int num : nums) {
            map.put(num, map.getOrDefault(num, 0) + 1);
        }
        for (int key : map.keySet()) {
            int frequence = map.get(key);
            if (bucket[frequence] == null) {
                bucket[frequence] = new ArrayList<>();
            }
            bucket[frequence].add(key);
        }
        List<Integer> res = new ArrayList<>();
        for (int pos = bucket.length - 1; pos >= 0 && res.size() < k; pos--) {
            if (bucket[pos] != null) {
                res.addAll(bucket[pos]);
            }
        }
        return res.stream().mapToInt(x -> x).toArray();
    }
}
```

{% hint style="success" %}
mapToInt()  returns an IntStream consisting of the results of applying the given function to the elements of this stream.
{% endhint %}

```
    public static void main(String[] args)
    {
  
        // Creating a list of Strings
        List<String> list = Arrays.asList("3", "6", "8", 
                                            "14", "15");
  
        // Using Stream mapToInt(ToIntFunction mapper)
        // and displaying the corresponding IntStream
        list.stream().mapToInt(num -> Integer.parseInt(num))
                     .filter(num -> num % 3 == 0)
                     .forEach(System.out::println);
    }
```

Follow ups：

1. 大数据无法全部放入内存hashmap处理 (MapReduce jobs)
   1. 先用data partitioner 将数据分开 分开到单台机器可以handle的size
   2. 使用multihost处理有一部分只存 B F A。另一部分存C D E。
   3.  再merge sort



       <figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

       <figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>
2. lookback window (在特定时间内 topK    【半小时前 2个小时前topK】)
   1. topK过来 到API Gateway 到storage&#x20;
   2.  分成快慢速时间段  （slow/fast path）

       1. slow path每小时做一次topK处理 用map Reduce处理 更加准确
       2. fast path每分钟做一次处理 performance 很好 但是data可能会有问题

       <figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>
3.
