# Search a 2D Matrix II

[https://leetcode.com/problems/search-a-2d-matrix-ii/](https://leetcode.com/problems/search-a-2d-matrix-ii/)

一个从上到下从左到右都排序过的Matrix

> Write an efficient algorithm that searches for a value `target` in an `m x n` integer matrix `matrix`. This matrix has the following properties:
>
> * Integers in each row are sorted in ascending from left to right.
> * Integers in each column are sorted in ascending from top to bottom.
>
> &#x20;
>
> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2020/11/24/searchgrid2.jpg)
>
> ```
> Input: matrix = [[1,4,7,11,15],[2,5,8,12,19],[3,6,9,16,22],[10,13,14,17,24],[18,21,23,26,30]], target = 5
> Output: true
> ```
>
> **Example 2:**
>
> ![](https://assets.leetcode.com/uploads/2020/11/24/searchgrid.jpg)
>
> ```
> Input: matrix = [[1,4,7,11,15],[2,5,8,12,19],[3,6,9,16,22],[10,13,14,17,24],[18,21,23,26,30]], target = 20
> Output: false
> ```

{% hint style="info" %}
简单点的方法是row遍历 然后每行进行二分 这样时间复杂度是 O(m\*log(n))

快速方法 从右上向左下找   右上到左下拉开左上的小右下的大  O(log(m \* n)) wrost O(m+n)

![0\_1488858509025\_Monosnap 2017-03-06 22-48-17.jpg](https://leetcode.com/uploads/files/1488858512318-monosnap-2017-03-06-22-48-17.jpg)![](<../.gitbook/assets/image (2) (1) (1).png>)
{% endhint %}

```
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        if(matrix == null || matrix.length == 0 || matrix[0].length == 0) return false;
        int row = matrix.length, col = matrix[0].length;
        int left = 0, right = col - 1;
        
        while(left < row && right >= 0){
            if(matrix[left][right] == target){
                return true;
            }else if(matrix[left][right] < target){
                left++;
            }else{
                right--;
            }
        }
        return false;
    }
}
```
