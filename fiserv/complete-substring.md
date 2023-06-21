# Complete Substring!

> **You are given two strings ‘S1’ and ‘S2’. Your task is to find the smallest substring of ‘S1’ which contains all the characters of ‘S2’. The characters of ‘S2’ need not be present in the same order in S1. That is, we need a substring that contains all characters of ‘S2’ irrespective of the order.**
>
> **A substring is a contiguous sequence of characters within a string.**
>
> **Example**
>
> ```
> Let ‘S1’ be “ABBCD” and ‘S2’ be “ABC”, so the smallest substring of ‘
> S1’ which contains all the characters of S1 is “ABBC”.
> ```

```
class Solution {
    public String minWindow(String s, String t) {
        if (t.length() > s.length()) return "";
        int[] cnt = new int[256];
        for (int i = 0; i < t.length(); i++) {
            cnt[t.charAt(i)]++;
        }
        int target = t.length();
        int len = Integer.MAX_VALUE;
        int head = 0;
        
        int l = 0, r = 0;
        while (r < s.length()) {
            if (cnt[s.charAt(r)] > 0) target--;
            cnt[s.charAt(r)]--;
            r++;
            while (target == 0) {
                if (len > r - l) {
                    len = r - l;
                    head = l;
                }
                cnt[s.charAt(l)]++;
                if (cnt[s.charAt(l)] > 0) target++;
                l++;
            }
        }
        if (len == Integer.MAX_VALUE) return "";
        return s.substring(head, head + len);
    }
}
```
