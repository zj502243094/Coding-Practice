# Valid Anagram

[https://leetcode.com/problems/valid-anagram/](https://leetcode.com/problems/valid-anagram/)

有效字谜 S T是否为乱序

> Given two strings `s` and `t`, return `true` _if_ `t` _is an anagram of_ `s`_, and_ `false` _otherwise_.
>
> An **Anagram** is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: s = "anagram", t = "nagaram"
> Output: true
> ```
>
> **Example 2:**
>
> ```
> Input: s = "rat", t = "car"
> Output: false
> ```

{% hint style="info" %}
出现在S的字母记录加一遍 在T里面减一遍&#x20;
{% endhint %}

```
class Solution {
    public boolean isAnagram(String s, String t) {
        int[] cnt = new int[256];
        for(int i = 0; i < s.length(); i++){
            cnt[s.charAt(i)]++;
        }
        for(int i = 0; i < t.length(); i++){
            cnt[t.charAt(i)]--;
        }
        for(int i = 0; i < 256; i++){
            if(cnt[i] != 0) return false;
        }
        return true;
    }
}
```
