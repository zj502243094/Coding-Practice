# Least Number of Unique Integers after K Removals

[https://leetcode.com/problems/least-number-of-unique-integers-after-k-removals/description/](https://leetcode.com/problems/least-number-of-unique-integers-after-k-removals/description/)\


> Given an array of integers `arr` and an integer `k`. Find the _least number of unique integers_ after removing **exactly** `k` elements.
>
> 1.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code><strong>Input: arr = [5,5,4], k = 1
> </strong><strong>Output: 1
> </strong><strong>Explanation: Remove the single 4, only 5 is left.
> </strong></code></pre>
>
> **Example 2:**
>
> <pre><code><strong>Input: arr = [4,3,1,1,3,3,2], k = 3
> </strong><strong>Output: 2
> </strong><strong>Explanation: Remove 4, 2 and either one of the two 1s or three 3s. 1 and 3 will be left.
> </strong></code></pre>

````
```java
class Solution {
    public int findLeastNumOfUniqueInts(int[] arr, int k) {
        Map<Integer, Integer> frequencyMap = new HashMap<>();

        // Step 1: Count the frequency of each element
        for (int num : arr) {
            frequencyMap.put(num, frequencyMap.getOrDefault(num, 0) + 1);
        }

        List<Integer> frequencies = new ArrayList<>(frequencyMap.values());

        // Step 2: Sort the frequencies in ascending order
        Collections.sort(frequencies);

        int uniqueCount = frequencies.size();

        // Step 3: Remove elements until k becomes zero or the frequencies are exhausted
        for (int i = 0; i < frequencies.size(); i++) {
            int frequency = frequencies.get(i);

            if (k >= frequency) {
                k -= frequency;
                uniqueCount--;
            } else {
                break;
            }
        }

        // Step 4: Return the number of remaining unique elements
        return uniqueCount;
    }
}
```
````
