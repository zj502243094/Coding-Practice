# Find All Anagrams in a String

[https://leetcode.com/problems/find-all-anagrams-in-a-string/](https://leetcode.com/problems/find-all-anagrams-in-a-string/)

> Given two strings `s` and `p`, return _an array of all the start indices of_ `p`_'s anagrams in_ `s`. You may return the answer in **any order**.
>
> An **Anagram** is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: s = "cbaebabacd", p = "abc"
> Output: [0,6]
> Explanation:
> The substring with start index = 0 is "cba", which is an anagram of "abc".
> The substring with start index = 6 is "bac", which is an anagram of "abc".
> ```
>
> **Example 2:**
>
> ```
> Input: s = "abab", p = "ab"
> Output: [0,1,2]
> Explanation:
> The substring with start index = 0 is "ab", which is an anagram of "ab".
> The substring with start index = 1 is "ba", which is an anagram of "ab".
> The substring with start index = 2 is "ab", which is an anagram of "ab".
> ```

```
class Solution {
    public List<Integer> findAnagrams(String s, String p) {
        List<Integer> res = new ArrayList<>();
        int[] cnt = new int[256];
        for(char c : p.toCharArray()) cnt[c]++;
        int target = p.length();
        
        int l = 0, r = 0;
        char[] sc = s.toCharArray();
        while(r < s.length()){
            if(cnt[sc[r]] > 0) target--;
            cnt[sc[r]]--;
            r++;
            while(target == 0) {
                if(r - l == p.length()) res.add(l);
                cnt[sc[l]]++;
                if(cnt[sc[l]] > 0) target++;
                l++;
            }
        }
        return res;
    }
}
```
