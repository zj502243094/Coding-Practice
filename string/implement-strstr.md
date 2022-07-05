# Implement strStr()

[https://leetcode.com/problems/implement-strstr/](https://leetcode.com/problems/implement-strstr/)

> Implement [strStr()](http://www.cplusplus.com/reference/cstring/strstr/).
>
> Given two strings `needle` and `haystack`, return the index of the first occurrence of `needle` in `haystack`, or `-1` if `needle` is not part of `haystack`.
>
> **Clarification:**
>
> What should we return when `needle` is an empty string? This is a great question to ask during an interview.
>
> For the purpose of this problem, we will return 0 when `needle` is an empty string. This is consistent to C's [strstr()](http://www.cplusplus.com/reference/cstring/strstr/) and Java's [indexOf()](https://docs.oracle.com/javase/7/docs/api/java/lang/String.html#indexOf\(java.lang.String\)).
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: haystack = "hello", needle = "ll"
> Output: 2
> ```
>
> **Example 2:**
>
> ```
> Input: haystack = "aaaaa", needle = "bba"
> Output: -1
> ```

```
class Solution {
    public int strStr(String source, String target) {
        if(source == null || target == null) return -1;
        
        for(int i = 0; i < source.length(); i++){
            if(i + target.length() > source.length()) return -1;
            for(int j = 0; j < target.length(); j++){
                if(source.charAt(i + j) != target.charAt(j)) break;
                if(j == target.length() - 1) return i;
            }
        }
        return -1;
        
    }
}
```
