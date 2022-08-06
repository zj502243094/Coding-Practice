# Top K Frequent Words

[https://leetcode.com/problems/top-k-frequent-words/](https://leetcode.com/problems/top-k-frequent-words/)

> Given an array of strings `words` and an integer `k`, return _the_ `k` _most frequent strings_.
>
> Return the answer **sorted** by **the frequency** from highest to lowest. Sort the words with the same frequency by their **lexicographical order**.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: words = ["i","love","leetcode","i","love","coding"], k = 2
> <strong>Output:
> </strong> ["i","love"]
> <strong>Explanation:
> </strong> "i" and "love" are the two most frequent words.
> Note that "i" comes before "love" due to a lower alphabetical order.</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: words = ["the","day","is","sunny","the","the","the","sunny","is","is"], k = 4
> <strong>Output:
> </strong> ["the","is","sunny","day"]
> <strong>Explanation:
> </strong> "the", "is", "sunny" and "day" are the four most frequent words, with the number of occurrence being 4, 3, 2 and 1 respectively.</code></pre>

```
class Solution {
    public List<String> topKFrequent(String[] words, int k) {
        List<String> res = new ArrayList<>();
        Map<String, Integer> map = new HashMap<>();
        for (String word : words) {
            map.put(word, map.getOrDefault(word, 0) + 1);
        }
        
        PriorityQueue<String> pq = new PriorityQueue<>(
            (w1, w2) -> map.get(w1).equals(map.get(w2)) ? w1.compareTo(w2) : map.get(w2) - map.get(w1)
        );
        for (String key : map.keySet()) {
            pq.offer(key);
        }
        for (int i = 0; i < k; i++) {
            res.add(pq.poll());
        }
        return res;
    }
}
```
