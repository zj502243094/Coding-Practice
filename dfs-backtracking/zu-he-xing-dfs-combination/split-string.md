# Split String

[https://www.jiuzhang.com/solution/split-string/](https://www.jiuzhang.com/solution/split-string/)

> Give a string, you can choose to split the string after one character or two adjacent characters, and make the string to be composed of only one character or two characters. Output all possible results.
>
> **样例**
>
> **Example1**
>
> ```
> Input: "123"
> Output: [["1","2","3"],["12","3"],["1","23"]]
> ```
>
> **Example2**
>
> ```
> Input: "12345"
> Output: [["1","23","45"],["12","3","45"],["12","34","5"],["1","2","3","45"],["1","2","34","5"],["1","23","4","5"],["12","3","4","5"],["1","2","3","4","5"]]
> ```

```
public List<List<String>> splitString(String s) {
        List<List<String>> res = new ArrayList<>();
        dfs(s, 0, new ArrayList<>(), res);
        return res;
    }
    private void dfs(String s, int index, List<String> cur, List<List<String>> res) {
        if (index == s.length()) {
            res.add(new ArrayList<>(cur));
            return;
        }
        cur.add(s.substring(index, index + 1));
        dfs(s, index + 1, cur, res);
        cur.remove(cur.size() - 1);
        
        if (index + 1 < s.length()) {
            cur.add(s.substring(index, index + 2));
            dfs(s, index + 2, cur, res);
            cur.remove(cur.size() - 1);
        }
    }
```
