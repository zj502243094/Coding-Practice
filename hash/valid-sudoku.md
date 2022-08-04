# Valid Sudoku

[https://leetcode.com/problems/valid-sudoku/](https://leetcode.com/problems/valid-sudoku/)

> Determine if a `9 x 9` Sudoku board is valid. Only the filled cells need to be validated **according to the following rules**:
>
> 1. Each row must contain the digits `1-9` without repetition.
> 2. Each column must contain the digits `1-9` without repetition.
> 3. Each of the nine `3 x 3` sub-boxes of the grid must contain the digits `1-9` without repetition.
>
> **Note:**
>
> * A Sudoku board (partially filled) could be valid but is not necessarily solvable.
> * Only the filled cells need to be validated according to the mentioned rules.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://upload.wikimedia.org/wikipedia/commons/thumb/f/ff/Sudoku-by-L2G-20050714.svg/250px-Sudoku-by-L2G-20050714.svg.png)

```
class Solution {
    public boolean isValidSudoku(char[][] board) {
        Set<String> set = new HashSet();
        for (int i = 0; i < 9; i++) {
            for (int j = 0; j < 9; j++) {
                char num = board[i][j];
                if (num != '.') {
                    if (!set.add(num + "in row" + i) 
                    || !set.add(num + "in col" + j) 
                    || !set.add(num + "in block" + i / 3 + j / 3))
                        return false;
                }
            }
        }
        return true;
    }
}
```
