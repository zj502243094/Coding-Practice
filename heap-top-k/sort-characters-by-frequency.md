# Sort Characters By Frequency

[https://leetcode.com/problems/sort-characters-by-frequency/](https://leetcode.com/problems/sort-characters-by-frequency/)

前面的套娃题 根据frequency排序

> Given a string `s`, sort it in **decreasing order** based on the **frequency** of the characters. The **frequency** of a character is the number of times it appears in the string.
>
> Return _the sorted string_. If there are multiple answers, return _any of them_.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: s = "tree"
> <strong>Output:
> </strong> "eert"
> <strong>Explanation:
> </strong> 'e' appears twice while 'r' and 't' both appear once.
> So 'e' must appear before both 'r' and 't'. Therefore "eetr" is also a valid answer.</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: s = "cccaaa"
> <strong>Output:
> </strong> "aaaccc"
> <strong>Explanation:
> </strong> Both 'c' and 'a' appear three times, so both "cccaaa" and "aaaccc" are valid answers.
> Note that "cacaca" is incorrect, as the same characters must be together.</code></pre>
>
> **Example 3:**
>
> <pre><code>Input: s = "Aabb"
> <strong>Output:
> </strong> "bbAa"
> <strong>Explanation:
> </strong> "bbaA" is also a valid answer, but "Aabb" is incorrect.
> Note that 'A' and 'a' are treated as two different characters.</code></pre>

{% hint style="info" %}
用PQ做，maxHeap 每次弹出来是频率最多的
{% endhint %}

```
class Solution {
    public String frequencySort(String s) {
        Map<Character, Integer> map = new HashMap<>();
        for (char c : s.toCharArray()) {
            map.put(c, map.getOrDefault(c, 0) + 1);
        }
        PriorityQueue<Character> pq = new PriorityQueue<>((a, b) -> map.get(b) - map.get(a));
        for (char key : map.keySet()) {
            pq.add(key);
        }
        StringBuilder sb = new StringBuilder();
        while (!pq.isEmpty()) {
            char c = pq.poll();
            for (int i = 0; i < map.get(c); i++) {
                sb.append(c);
            }
        }
        return sb.toString();
    }
}
```

```
class Solution {
    public String frequencySort(String s) {
        Map<Character, Integer> map = new HashMap<>();
        for (char c : s.toCharArray()) {
            map.put(c, map.getOrDefault(c, 0) + 1);
        }
        List<Character>[] bucket = new List[s.length() + 1];
        for (char key : map.keySet()) {
            int frequence = map.get(key);
            if (bucket[frequence] == null) bucket[frequence] = new ArrayList<>();
            bucket[frequence].add(key);
        }
        StringBuilder sb = new StringBuilder();
        for (int pos = bucket.length - 1; pos >= 0; pos--) {
            if (bucket[pos] != null) {
                for (char c : bucket[pos]) {
                    for (int i = 0; i < pos; i++) {
                        sb.append(c);
                    }
                }
            }
        }
        return sb.toString();
    }
}
```
