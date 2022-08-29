# Lexicographical Numbers

[https://leetcode.com/problems/lexicographical-numbers/](https://leetcode.com/problems/lexicographical-numbers/)

按字典序排序

> Given an integer `n`, return all the numbers in the range `[1, n]` sorted in lexicographical order.
>
> You must write an algorithm that runs in `O(n)` time and uses `O(1)` extra space.&#x20;
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: n = 13
> <strong>Output: [1,10,11,12,13,2,3,4,5,6,7,8,9]</strong></code></pre>
>
> **Example 2:**
>
> <pre><code>Input: n = 2
> <strong>Output: [1,2]</strong></code></pre>

```
class Solution {
    public List<Integer> lexicalOrder(int n) {
        String[] str = new String[n];
        for (int i = 1; i <= n; i++) {
            str[i - 1] = Integer.toString(i);
        }
        Arrays.sort(str);
        List<Integer> res = new ArrayList<>();
        for (String s : str) {
            res.add(Integer.parseInt(s));
        }
        return res;
    }
}
```

```
class Solution {
    public List<Integer> lexicalOrder(int n) {
        List<Integer> res = new ArrayList<>();
        for (int i = 1; i < 10; i++) {
            dfs (n, i, res);
        }
        return res;
    }
    private void dfs(int n, int cur, List<Integer> res) {
        if (cur > n) return;
        res.add(cur);
        for (int i = 0; i < 10; i++) {
            if (10 * cur + i > n) return;
            dfs(n, 10 * cur + i, res);
        }
    }
}
```
