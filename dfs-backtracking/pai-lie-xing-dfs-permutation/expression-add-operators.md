# Expression Add Operators

[https://leetcode.com/problems/expression-add-operators/](https://leetcode.com/problems/expression-add-operators/)

> Given a string `num` that contains only digits and an integer `target`, return _**all possibilities** to insert the binary operators_ `'+'`_,_ `'-'`_, and/or_ `'*'` _between the digits of_ `num` _so that the resultant expression evaluates to the_ `target` _value_.
>
> Note that operands in the returned expressions **should not** contain leading zeros.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: num = "123", target = 6
> <strong>Output:
> </strong> ["1*2*3","1+2+3"]
> <strong>Explanation:
> </strong> Both "1*2*3" and "1+2+3" evaluate to 6.</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: num = "232", target = 8
> <strong>Output:
> </strong> ["2*3+2","2+3*2"]
> <strong>Explanation:
> </strong> Both "2*3+2" and "2+3*2" evaluate to 8.</code></pre>

```
class Solution {
    public List<String> addOperators(String num, int target) {
        List<String> res = new ArrayList<>();
        dfs(num, target, 0, "", 0, 0, res);
        return res;
    }
    private void dfs(String num, int target, int index, String cur, long sum, long last, List<String> res) {
        if (index == num.length()) {
            if (sum == target) {
                res.add(cur);
            }
            return;
        }
        for (int i = index; i < num.length(); i++) {
            long x = Long.parseLong(num.substring(index, i + 1));
            if (index == 0) {
                dfs(num, target, i + 1, cur + x, x, x, res);
            } else {
                dfs(num, target, i + 1, cur + "+" + x, sum + x, x, res);
                dfs(num, target, i + 1, cur + "-" + x, sum - x, -x, res);
                dfs(num, target, i + 1, cur + "*" + x, sum - last + last * x, last * x, res);
            }
            if (x == 0) {
                break;
            }
        }
    }
}
```
