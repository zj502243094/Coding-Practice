# Majority Element II

> Given an integer array of size `n`, find all elements that appear more than `⌊ n/3 ⌋` times.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code>Input: nums = [3,2,3]
> <strong>Output:
> </strong> [3]</code></pre>
>
> **Example 2:**
>
> <pre><code>Input: nums = [1]
> <strong>Output:
> </strong> [1]</code></pre>
>
> **Example 3:**
>
> <pre><code>Input: nums = [1,2]
> <strong>Output:
> </strong> [1,2]</code></pre>

```
class Solution {
    public List<Integer> majorityElement(int[] nums) {
        List<Integer> res = new ArrayList<>();
        int n1 = 0, n2 = 0;
        int s1 = 0, s2 = 0;
        for (int num : nums) {
            if (num == n1) {
                s1++;
            } else if (num == n2) {
                s2++;
            } else if (s1 == 0) {
                n1 = num;
                s1 = 1;
            } else if (s2 == 0) {
                n2 = num;
                s2 = 1;
            } else {
                s1--;
                s2--;
            }
        }
        s1 = 0;
        s2 = 0;
        for (int num : nums) {
            if (num == n1) {
                s1++;
            } else if (num == n2) {
                s2++;
            }
        }
        if (s1 > nums.length / 3) {
            res.add(n1);
        }
        if (s2 > nums.length / 3) {
            res.add(n2);
        }
        return res;
    }
}
```
