# Top k Largest Numbers

> Given an integer array, find the top k largest numbers in it.
>
> **Example**
>
> Given \[3,10,1000,-99,4,100] and k = 3. Return \[1000, 100, 10].

```
class Solution {
    public int findKthLargest(int[] nums, int k) {
        
        PriorityQueue<Integer> pq = new PriorityQueue<>(Collections.reverseOrder());
        for (int num : nums) {
            pq.offer(num);
        }
        int[] res = new int[k];
        for (int i = 0; i < k; i++) {
            res[i] = pq.poll();
        }
        return res;
    }
}
```
