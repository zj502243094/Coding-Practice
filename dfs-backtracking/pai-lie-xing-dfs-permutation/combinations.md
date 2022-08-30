# Combinations

[https://leetcode.com/problems/combinations/](https://leetcode.com/problems/combinations/)

> Given two integers `n` and `k`, return _all possible combinations of_ `k` _numbers chosen from the range_ `[1, n]`.
>
> You may return the answer in **any order**.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: n = 4, k = 2
> <strong>Output: [[1,2],[1,3],[1,4],[2,3],[2,4],[3,4]]
> </strong><strong>Explanation:
> </strong> There are 4 choose 2 = 6 total combinations.
> Note that combinations are unordered, i.e., [1,2] and [2,1] are considered to be the same combination.</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: n = 1, k = 1
> <strong>Output: [[1]]
> </strong><strong>Explanation:
> </strong> There is 1 choose 1 = 1 total combination.</code></pre>

```
class Solution {
    public List<List<Integer>> combine(int n, int k) {
        List<List<Integer>> res = new ArrayList<>();
        dfs(n, k, 1, new ArrayList<>(), res);
        return res;
    }
    private void dfs(int n, int k, int index, List<Integer> cur, List<List<Integer>> res) {
        if (cur.size() == k) {
            res.add(new ArrayList<>(cur));
            return;
        }
        for (int i = index; i <= n; i++) {
            cur.add(i);
            dfs(n, k, i + 1, cur, res);
            cur.remove(cur.size() - 1);
        }
    }
}
```
