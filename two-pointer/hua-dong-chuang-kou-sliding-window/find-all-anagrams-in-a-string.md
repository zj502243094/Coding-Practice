# Find All Anagrams in a String

[https://leetcode.com/problems/find-all-anagrams-in-a-string/](https://leetcode.com/problems/find-all-anagrams-in-a-string/)

在一个字符串中找到全部乱序数组 的位置

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

{% hint style="info" %}
记录一遍P的的字母数

遍历字符串S 当r在P中出现过 target -- 到target == 0

直到 r - l == p.length() 左端点开始移动 有重复数字出现 重新循环
{% endhint %}

```
class Solution {
    public List<Integer> findAnagrams(String s, String p) {
        List<Integer> res = new ArrayList<>();
        if (s.length() < p.length()) return res;
        int[] cnt = new int[256];
        for (int i = 0; i < p.length(); i++) {
            cnt[p.charAt(i)]++;
        }
        int target = p.length();
        
        int l = 0, r = 0;
        while (r < s.length()) {
            if (cnt[s.charAt(r)] > 0) target--;
            cnt[s.charAt(r)]--;
            r++;
            while (target == 0) {
                if (r - l == p.length()) res.add(l);
                cnt[s.charAt(l)]++;
                if (cnt[s.charAt(l)] > 0) target++;
                l++;
            }
        }
        return res;
    }
}
```

{% hint style="info" %}
建一个map 字符和出现次数
{% endhint %}

```
class Solution {
    public List<Integer> findAnagrams(String s, String p) {
        List<Integer> res = new ArrayList<>();
        Map<Character, Integer> map = new HashMap();
        for (char c : p.toCharArray()) {
            map.put(c, map.getOrDefault(c, 0) + 1);
        }
        int target = map.size();
        
        int l = 0, r = 0;
        while(r < s.length()) {
            char c = s.charAt(r);
            if (map.containsKey(c)) {
                map.put(c, map.get(c) - 1);
                if (map.get(c) == 0) target--;
            }
            r++;
            while (target == 0) {
                char tmpc = s.charAt(l);
                if(map.containsKey(tmpc)){
                    map.put(tmpc, map.get(tmpc) + 1);
                    if (map.get(tmpc) > 0) target++;
                }
                if(r - l == p.length()) res.add(l);
                l++;
            }
        }
        return res;
    }
}
```
