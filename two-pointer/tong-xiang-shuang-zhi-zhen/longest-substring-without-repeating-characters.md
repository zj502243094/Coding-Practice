# Longest Substring Without Repeating Characters

[https://leetcode.com/problems/longest-substring-without-repeating-characters/](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

找到最长不重复的 sub

> Given a string `s`, find the length of the **longest substring** without repeating characters.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: s = "abcabcbb"
> Output: 3
> Explanation: The answer is "abc", with the length of 3.
> ```
>
> **Example 2:**
>
> ```
> Input: s = "bbbbb"
> Output: 1
> Explanation: The answer is "b", with the length of 1.
> ```
>
> **Example 3:**
>
> ```
> Input: s = "pwwkew"
> Output: 3
> ```

```
class Solution {
    public int lengthOfLongestSubstring(String s) {
        if(s == null || s.length() == 0) return 0;
        int[] cnt = new int[256];
        int res = 0;
        
        int l = 0, r = 0;
        while(r < s.length()){
            cnt[s.charAt(r)]++;
            while(l <= r && cnt[s.charAt(r)] > 1){
                cnt[s.charAt(l)]--;
                l++;
            }
            res = Math.max(res, r - l + 1);
            r++;
        }
        return res;
    }
}
```

```
public int lengthOfLongestSubstring(String s) {
        if (s == null) return 0;
        
        char[] sc = s.toCharArray();
        int maxSize = Integer.MIN_VALUE;
        Set<Character> set = new HashSet<>();
        
        for (int l = 0, r = 0; r < sc.length; r++) {
            while (set.contains(sc[r])) {
                set.remove(sc[l++]);
            }
            set.add(sc[r]);
            maxSize = Math.max(maxSize, set.size());
        }
        return maxSize == Integer.MIN_VALUE ? 0 : maxSize;
    }
```
