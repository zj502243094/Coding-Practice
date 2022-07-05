# Reverse Words in a String II

[https://leetcode.com/problems/reverse-words-in-a-string-ii/](https://leetcode.com/problems/reverse-words-in-a-string-ii/)

> Given a string `s`, reverse the order of characters in each word within a sentence while still preserving whitespace and initial word order.
>
> &#x20;
>
> **Example 1:**
>
> ```
> Input: s = "Let's take LeetCode contest"
> Output: "s'teL ekat edoCteeL tsetnoc"
> ```
>
> **Example 2:**
>
> ```
> Input: s = "God Ding"
> Output: "doG gniD"
> ```

```
class Solution {
    public String reverseWords(String s) {
        if(s == null || s.length() == 0) return s;
        String[] words = s.split(" ");
        StringBuffer sb = new StringBuffer();
        
        for(int i = 0; i < words.length; i++){
            if(!words[i].isEmpty()){
                if(sb.length() > 0){
                    sb.append(" ");
                }
                sb.append(reverse(words[i]));
            }
        }
        return sb.toString();
    }
    private String reverse(String s){
        char[] c = s.toCharArray();
        int i = 0;
        int j = c.length - 1;
        while(i < j){
            char tmp = c[i];
            c[i] = c[j];
            c[j] = tmp;
            i++;
            j--;
        }
        return String.valueOf(c);
    }
}
```
