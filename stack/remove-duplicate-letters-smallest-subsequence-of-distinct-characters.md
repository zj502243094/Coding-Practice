# Remove Duplicate Letters / Smallest Subsequence of Distinct Characters

[https://leetcode.com/problems/remove-duplicate-letters/](https://leetcode.com/problems/remove-duplicate-letters/)

[https://leetcode.com/problems/smallest-subsequence-of-distinct-characters/](https://leetcode.com/problems/smallest-subsequence-of-distinct-characters/)

> Given a string `s`, remove duplicate letters so that every letter appears once and only once. You must make sure your result is **the smallest in lexicographical order** among all possible results.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: s = "bcabc"
> <strong>Output:
> </strong> "abc"</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: s = "cbacdcbc"
> <strong>Output:
> </strong> "acdb"</code></pre>

> Given a string `s`, return _the lexicographically smallest subsequence of_ `s` _that contains all the distinct characters of_ `s` _exactly once_.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: s = "bcabc"
> <strong>Output:
> </strong> "abc"</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: s = "cbacdcbc"
> <strong>Output:
> </strong> "acdb"</code></pre>

{% hint style="info" %}
last 是 每个字母最后出现的位置
{% endhint %}

```
class Solution {
    public String smallestSubsequence(String s) {
        Stack<Integer> stack = new Stack<>();
        int[] last = new int[128];
        Set<Integer> visit = new HashSet<>();
        for (int i = 0; i < s.length(); i++) {
            last[s.charAt(i)] = i;
        } 
        for (int i = 0; i < s.length(); i++) {
            int c = s.charAt(i);
            if (!visit.add(c)) continue;
            while (!stack.isEmpty() && c < stack.peek() && i < last[stack.peek()]) visit.remove(stack.pop());
            stack.push(c);
        }
        StringBuilder sb = new StringBuilder();
        for (int i : stack) sb.append((char)(i));
        return sb.toString();
    }
}
```
