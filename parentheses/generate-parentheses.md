# Generate Parentheses

[https://leetcode.com/problems/generate-parentheses/](https://leetcode.com/problems/generate-parentheses/)

> Given `n` pairs of parentheses, write a function to _generate all combinations of well-formed parentheses_.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: n = 3
> <strong>Output:
> </strong> ["((()))","(()())","(())()","()(())","()()()"]</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: n = 1
> <strong>Output:
> </strong> ["()"]</code></pre>

{% hint style="info" %}
左括号 只要小于N 就可以加

右括号 需要小于N 并且 个数小于左括号
{% endhint %}

```
class Solution {
    public List<String> generateParenthesis(int n) {
        List<String> res = new ArrayList<>();
        dfs(n, "", 0, 0, res);
        return res;
    }
    private void dfs(int n, String cur, int left, int right, List<String> res) {
        if (left == n && right == n) {
            res.add(cur);
            return;
        }
        if (left < n) {
            dfs(n, cur + "(", left + 1, right, res);
        }
        if (right < n && right < left) {
            dfs(n, cur + ")", left, right + 1, res);
        }
    }
}
```

```
class Solution {
    public List<String> generateParenthesis(int n) {
        List<String> res = new ArrayList<>();
        dfs(n, "", 0, 0, res);
        return res;
    }
    private void dfs(int n, String cur, int left, int right, List<String> res) {
        if (left == n && right == n) {
            res.add(cur);
            return;
        }
        if (left < n) {
            dfs(n, cur + "(", left + 1, right, res);
        }
        if (right < left) {
            dfs(n, cur + ")", left, right + 1, res);
        }
    }
}
```
