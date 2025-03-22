# Baseball Game

[https://leetcode.com/problems/baseball-game/description/](https://leetcode.com/problems/baseball-game/description/)

> You are keeping the scores for a baseball game with strange rules. At the beginning of the game, you start with an empty record.
>
> You are given a list of strings `operations`, where `operations[i]` is the `ith` operation you must apply to the record and is one of the following:
>
> * An integer `x`.
>   * Record a new score of `x`.
> * `'+'`.
>   * Record a new score that is the sum of the previous two scores.
> * `'D'`.
>   * Record a new score that is the double of the previous score.
> * `'C'`.
>   * Invalidate the previous score, removing it from the record.
>
> Return _the sum of all the scores on the record after applying all the operations_.
>
> The test cases are generated such that the answer and all intermediate calculations fit in a **32-bit** integer and that all operations are valid.
>
> &#x20;
>
> **Example 1:**
>
> <pre><code><strong>Input: ops = ["5","2","C","D","+"]
> </strong><strong>Output: 30
> </strong><strong>Explanation:
> </strong>"5" - Add 5 to the record, record is now [5].
> "2" - Add 2 to the record, record is now [5, 2].
> "C" - Invalidate and remove the previous score, record is now [5].
> "D" - Add 2 * 5 = 10 to the record, record is now [5, 10].
> "+" - Add 5 + 10 = 15 to the record, record is now [5, 10, 15].
> The total sum is 5 + 10 + 15 = 30.
> </code></pre>

```
class Solution {
    public int calPoints(String[] operations) {
        Stack<Integer> stack = new Stack<>();
        for (String op : operations) {
            if (op.equals("C")) {
                stack.pop();  // Remove the last score
            } else if (op.equals("D")) {
                stack.push(2 * stack.peek());  // Double the last score
            } else if (op.equals("+")) {
                int last = stack.pop();
                int secondLast = stack.peek();
                int newScore = last + secondLast;
                stack.push(last);  // Push back the last score
                stack.push(newScore);
            } else {
                stack.push(Integer.parseInt(op));  // Convert string to integer and push
            }
        }
        int sum = 0;
        for (int score : stack) {
            sum += score;
        }
        return sum;
    }
}
```
