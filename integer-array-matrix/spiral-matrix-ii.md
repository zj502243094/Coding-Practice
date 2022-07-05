# Spiral Matrix II

[https://leetcode.com/problems/spiral-matrix-ii/](https://leetcode.com/problems/spiral-matrix-ii/)

> Given a positive integer `n`, generate an `n x n` `matrix` filled with elements from `1` to `n2` in spiral order.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2020/11/13/spiraln.jpg)
>
> ```
> Input: n = 3
> Output: [[1,2,3],[8,9,4],[7,6,5]]
> ```
>
> **Example 2:**
>
> ```
> Input: n = 1
> Output: [[1]]
> ```

```
class Solution {
    public int[][] generateMatrix(int n) {
        int[][] res = new int[n][n];
        int rowB = 0;
        int rowE = n - 1;
        int colB = 0;
        int colE = n - 1;
        int num = 1;
        
        while(rowB <= rowE && colB <= colE){
            for(int i = colB; i <= colE; i++){
                res[rowB][i] = num++;
            }
            rowB++;
            for(int i = rowB; i <= rowE; i++){
                res[i][colE] = num++;
            }
            colE--;
            for(int i = colE; i >= colB; i--){
                res[rowE][i] = num++;
            }
            rowE--;
            for(int i = rowE; i >= rowB; i--){
                res[i][colB] = num++;
            }
            colB++;
        }
        return res;
    }
}
```
