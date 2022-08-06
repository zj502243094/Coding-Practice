# K Closest Points to Origin

[https://leetcode.com/problems/k-closest-points-to-origin/](https://leetcode.com/problems/k-closest-points-to-origin/)

> **Example 1:**
>
> ![](https://assets.leetcode.com/uploads/2021/03/03/closestplane1.jpg)
>
> <pre><code>Input: points = [[1,3],[-2,2]], k = 1
> <strong>Output: [[-2,2]]</strong></code></pre>

```
class Solution {
    public int[][] kClosest(int[][] points, int k) {
        int[][] res = new int[k][];
        PriorityQueue<int[]> pq = new PriorityQueue<int[]>(
            (a, b) -> ((b[0]*b[0] + b[1]*b[1]) - (a[0]*a[0] + a[1]*a[1]))
        );
        
        for (int[] point : points) {
            pq.offer(point);
            if (pq.size() > k) {
                pq.poll();
            }
        }
        for (int i = 0; i < k; i++) {
            res[i] = pq.poll();
        }
        return res;
    }
}
```
