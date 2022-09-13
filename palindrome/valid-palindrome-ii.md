# Valid Palindrome II

[https://leetcode.com/problems/valid-palindrome-ii/](https://leetcode.com/problems/valid-palindrome-ii/)

去掉一个字符后 是否为回文串

> Given a string `s`, return `true` _if the_ `s` _can be palindrome after deleting **at most one** character from it_.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: s = "aba"
> Output: true
> ```
>
> **Example 2:**
>
> ```
> Input: s = "abca"
> Output: true
> Explanation: You could delete the character 'c'.
> ```
>
> **Example 3:**
>
> ```
> Input: s = "abc"
> Output: false
> ```

```
class Solution {
    public boolean validPalindrome(String s) {
        if(s == null || s.length() == 0) return true;
        int l = 0, r = s.length() - 1;
        while(l < r){
            if(s.charAt(l) == s.charAt(r)){
                l++;
                r--;
            }else{
               return isPalinrome(s, l + 1, r) || isPalinrome(s, l, r - 1); 
            }
        }
        return true;
    } 
    private boolean isPalinrome(String s, int l, int r){
        while(l < r){
            if(s.charAt(l) == s.charAt(r)){
                l++;
                r--;
            }else{
                return false;
            }
        }
        return true;
    }
}
```
