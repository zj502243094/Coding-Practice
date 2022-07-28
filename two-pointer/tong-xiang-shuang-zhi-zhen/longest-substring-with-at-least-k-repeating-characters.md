# Longest Substring with At Least K Repeating Characters

[https://leetcode.com/problems/longest-substring-with-at-least-k-repeating-characters/](https://leetcode.com/problems/longest-substring-with-at-least-k-repeating-characters/)

> Given a string `s` and an integer `k`, return _the length of the longest substring of_ `s` _such that the frequency of each character in this substring is greater than or equal to_ `k`.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: s = "aaabb", k = 3
> Output: 3
> Explanation: The longest substring is "aaa", as 'a' is repeated 3 times.
> ```
>
> **Example 2:**
>
> ```
> Input: s = "ababbc", k = 2
> Output: 5
> Explanation: The longest substring is "ababb", as 'a' is repeated 2 times and 'b' is repeated 3 times.
> ```

```
class Solution {
    public int longestSubstring(String s, int k) {
        if (s.length() < k) return 0;
        int[] cnt = new int[256];
        for (int i = 0; i < s.length(); i++) {
            cnt[s.charAt(i)]++;
        }
        for (int i = 0; i < s.length(); i++) {
            if (cnt[s.charAt(i)] >= k) continue;
            int j = i + 1;
            while (j < s.length() && cnt[s.charAt(j)] < k) j++;
            return Math.max(longestSubstring(s.substring(0, i), k), longestSubstring(s.substring(j), k));
        }
        return s.length();
    }
}
```
