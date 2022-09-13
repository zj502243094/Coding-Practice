# Palindrome Partitioning

[https://leetcode.com/problems/palindrome-partitioning/](https://leetcode.com/problems/palindrome-partitioning/)

回文串拆分 使拆开的每一个子串都是回文串

> Given a string `s`, partition `s` such that every substring of the partition is a **palindrome**. Return all possible palindrome partitioning of `s`.
>
> A **palindrome** string is a string that reads the same backward as forward.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: s = "aab"
> <strong>Output: [["a","a","b"],["aa","b"]]</strong></code></pre>
>
> **Example 2:**
>
> <pre><code>Input: s = "a"
> <strong>Output: [["a"]]</strong></code></pre>

{% hint style="info" %}
按位置选 第一次从0 选 1个 a/2个 aa/ 3个 aab

第二次 从1位置开始选 a ab  第三次从2位置选 b
{% endhint %}

&#x20;![](<../.gitbook/assets/Screen Shot 2022-08-20 at 11.53.19 PM.png>)

```
class Solution {
    public List<List<String>> partition(String s) {
        List<List<String>> res = new ArrayList<>();
        dfs(s, 0, new ArrayList<>(), res);
        return res;
    }
    private void dfs(String s, int index, List<String> cur, List<List<String>> res) {
        if (index == s.length()) {
            res.add(new ArrayList<>(cur));
        }
        for (int i = index; i < s.length(); i++) {
            String subStr = s.substring(index, i + 1);
            if (isPalindrome(subStr)) {
                cur.add(subStr);
                dfs (s, i + 1, cur, res);
                cur.remove(cur.size() - 1);
            }
        }
    }
    private boolean isPalindrome(String s) {
        int l = 0, r = s.length() - 1;
        while (l < r) {
            if (s.charAt(l) != s.charAt(r)) {
                return false;
            }
            l++;
            r--;
        } 
        return true;
    }
}
```
