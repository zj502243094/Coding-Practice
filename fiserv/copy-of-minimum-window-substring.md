# Copy of Minimum Window Substring

[https://leetcode.com/problems/minimum-window-substring/](https://leetcode.com/problems/minimum-window-substring/)

最短包含T的 substring的字符串

> Given two strings `s` and `t` of lengths `m` and `n` respectively, return _the **minimum window substring** of_ `s` _such that every character in_ `t` _(**including duplicates**) is included in the window. If there is no such substring, return the empty string_ `""`
>
>
>
> **Example 1:**
>
> ```
> Input: s = "ADOBECODEBANC", t = "ABC"
> Output: "BANC"
> Explanation: The minimum window substring "BANC" includes 'A', 'B', and 'C' from string t.
> ```
>
> **Example 2:**
>
> ```
> Input: s = "a", t = "a"
> Output: "a"
> Explanation: The entire string s is the minimum window.
> ```
>
> **Example 3:**
>
> ```
> Input: s = "a", t = "aa"
> Output: ""
> ```

```
class Solution {
    public String minWindow(String s, String t) {
        if(t.length() > s.length()) return "";
        int[] cnt = new int[256];
        for(char c : t.toCharArray()) cnt[c]++;
        int l = 0, r = 0;
        int len = Integer.MAX_VALUE;
        int target = t.length();
        int head = 0;
        
        while (r < s.length()){
            if (cnt[s.charAt(r)] > 0) target--;
            cnt[s.charAt(r)]--;
            r++;
            while (target == 0) {
                if (r - l < len) {
                    len = r - l;
                    head = l;
                }
                cnt[s.charAt(l)]++;
                if(cnt[s.charAt(l)] > 0) target++;
                l++;
            }
        }
        if (len == Integer.MAX_VALUE) return "";
        return s.substring(head, head + len);
    }
}
```
