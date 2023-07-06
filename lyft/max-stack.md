# Max Stack

[https://leetcode.com/problems/max-stack/](https://leetcode.com/problems/max-stack/)

{% hint style="info" %}
&#x20;唯一多出来的 popMax()  删去maxStack 的同时 stack 中这个最大的元素也要删掉\
所以在stack中每次弹出的元素要保留在一个tmp stack里面
{% endhint %}

```
class MaxStack {
    Stack<Integer> stack;
    Stack<Integer> maxStack;

    public MaxStack() {
        stack = new Stack();
        maxStack = new Stack();
    }
    
    public void push(int x) {
        stack.push(x);
        if(maxStack.isEmpty()) {
            maxStack.push(x);
        } else {
            maxStack.push(Math.max(maxStack.peek(), x));
        }
    }
    
    public int pop() {
        maxStack.pop();
        return stack.pop();
    }
    
    public int top() {
        return stack.peek();
    }
    
    public int peekMax() {
        return maxStack.peek();
    }
    
    public int popMax() {
        int max = peekMax();
        Stack<Integer> tmp = new Stack();
        while(top() != max) tmp.push(pop());
        pop();
        while(!tmp.isEmpty()) push(tmp.pop());
        return max;
    }
}
```
