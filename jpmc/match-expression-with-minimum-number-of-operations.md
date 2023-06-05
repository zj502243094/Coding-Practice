# Match Expression with minimum number of operations

> An expression is said to be matched if for every '>' there is a corresponding '<' to the left it. Example of a matched expression is <<><>>. Say you have an unmatched expression eg <>>, then can you convert it to a matched expression&#x20;
>
> if the only operation you can do is replace a '>' with a '<>'.&#x20;
>
> Two arrays were given: expressionsArray, maxReplacements both were of the same length. We had to iterate through the expressionsArray and check if we can return a balanced expression (say for expressionsArray\[i] if we are allowed to execute the above mentioned operation only maxReplacements\[i] number of times. Return a boolean array indicating if it is possible.
>
> eg)&#x20;
>
> expressionsArr = \["<<>" , "<<><><<>>>", "<>>>"]&#x20;
>
> maxReplacements = \[1,0,2]&#x20;
>
> Answer = \[False, True, True]

```
public static boolean[] isBalancedExpressions(String[] expressionsArr, int[] maxReplacements) {
        boolean[] result = new boolean[expressionsArr.length];

        for (int i = 0; i < expressionsArr.length; i++) {
            String expression = expressionsArr[i];
            int replacements = maxReplacements[i];
            int unmatchedCount = 0;

            Stack<Character> stack = new Stack<>();

            for (char c : expression.toCharArray()) {
                if (c == '<') {
                    stack.push(c);
                } else if (c == '>') {
                    if (!stack.isEmpty()) {
                        stack.pop();
                    } else {
                        unmatchedCount++;
                    }
                }
            }

            if (stack.isEmpty() && unmatchedCount <= replacements) {
                result[i] = true;
            }
        }

        return result;
    }
    
public static void main(String[] args) {

        String[] expressionsArr = {"<<>", "<<><><<>>>", "<>>>"};
        int[] maxReplacements = {1, 0, 2};

        boolean[] result = isBalancedExpressions(expressionsArr, maxReplacements);

        for (boolean res : result) {
            System.out.println(res);
        }
    }
```
