# Kth Smallest Element in a Sorted Matrix

[https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/](https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/)

> Given an `n x n` `matrix` where each of the rows and columns is sorted in ascending order, return _the_ `kth` _smallest element in the matrix_.
>
> Note that it is the `kth` smallest element **in the sorted order**, not the `kth` **distinct** element.
>
> You must find a solution with a memory complexity better than `O(n2)`.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: matrix = [[1,5,9],[10,11,13],[12,13,15]], k = 8
> <strong>Output:13
> </strong><strong>Explanation:
> </strong> The elements in the matrix are [1,5,9,10,11,12,13,13,15], and the 8th smallest number is 13</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: matrix = [[-5]], k = 1
> <strong>Output:-5</strong></code></pre>

```
class Solution {
    public int kthSmallest(int[][] matrix, int k) {
        PriorityQueue<Integer> pq = new PriorityQueue();
        for (int i = 0; i < matrix.length; i++) {
            for (int j = 0; j < matrix[0].length; j++) {
                pq.offer(matrix[i][j]);
            }
        }
        
        int res = Integer.MAX_VALUE;
        for (int i = 0; i < k; i++) {
            res = pq.poll();
        }
        return res;
    }
}
```
