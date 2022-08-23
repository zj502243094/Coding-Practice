# First Unique Character in a String

[https://leetcode.com/problems/first-unique-character-in-a-string/](https://leetcode.com/problems/first-unique-character-in-a-string/)

> Given a string `s`, _find the first non-repeating character in it and return its index_. If it does not exist, return `-1`.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: s = "leetcode"
> Output: 0
> ```
>
> **Example 2:**
>
> ```
> Input: s = "loveleetcode"
> Output: 2
> ```
>
> **Example 3:**
>
> ```
> Input: s = "aabb"
> Output: -1
> ```

```
class Solution {
    public int firstUniqChar(String s) {
        int res = -1;
        int[] cnt = new int[256];
        for(char c : s.toCharArray()) cnt[c]++;
        for (int i = 0; i < s.length(); i++) {
            if(cnt[s.charAt(i)] == 1) {
                res = i;
                break;
            }   
        }
        return res;
    }
}
```
