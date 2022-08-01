# Longest Substring with At Most K Distinct Characters

[https://leetcode.com/problems/longest-substring-with-at-most-k-distinct-characters/](https://leetcode.com/problems/longest-substring-with-at-most-k-distinct-characters/)

> Given a string `s` and an integer `k`, return _the length of the longest substring of_ `s` _that contains at most_ `k` _**distinct** characters_.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: s = "eceba", k = 2
> Output: 3
> Explanation: The substring is "ece" with length 3.
> ```
>
> **Example 2:**
>
> ```
> Input: s = "aa", k = 1
> Output: 2
> Explanation: The substring is "aa" with length 2.
> ```

{% hint style="info" %}
记录每个字符出现的次数 然后 出现过一次就将 代表有几个字母的sum++\
超过K后 将左端点开始移动 直到 左端点字符出现数 为 0 然后 sum--； 变为K&#x20;
{% endhint %}

```
class Solution {
    public int lengthOfLongestSubstringKDistinct(String s, int k) {
        if(s == null || s.length() == 0) return 0;
        int[] cnt = new int[256];
        int res = 0;
        
        int l = 0, r = 0;
        int sum = 0;
        while(r < s.length()){
            cnt[s.charAt(r)]++;
            if(cnt[s.charAt(r)] == 1) sum++;
            while(l <= r && sum > k){
                cnt[s.charAt(l)]--;
                if(cnt[s.charAt(l)] == 0) sum--;
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
class Solution {
    public int lengthOfLongestSubstringKDistinct(String s, int k) {
        if(s == null || s.length() == 0) return 0;
        int[] cnt = new int[256];
        int res = 0;
        
        int sum = 0;
        int l = 0;
        for (int r = 0; r < s.length(); r++) {
            cnt[s.charAt(r)]++;
            if (cnt[s.charAt(r)] == 1) sum++;
            while (sum > k) {
                cnt[s.charAt(l)]--;
                if (cnt[s.charAt(l)] == 0) sum--;
                l++;
            }
            res = Math.max(res, r - l + 1);
        }
        return res;
    }
}
```
