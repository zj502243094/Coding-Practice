# Min Stack

[https://leetcode.com/problems/min-stack/](https://leetcode.com/problems/min-stack/)

实现一个stack 还有 额外的getMin() 功能

> Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.
>
> Implement the `MinStack` class:
>
> * `MinStack()` initializes the stack object.
> * `void push(int val)` pushes the element `val` onto the stack.
> * `void pop()` removes the element on the top of the stack.
> * `int top()` gets the top element of the stack.
> * `int getMin()` retrieves the minimum element in the stack.

{% hint style="info" %}
用2个 stack 一个普通stack 一个minStack 插入时每次同时维护两个栈 minStack为最小值\
stack :        \[2 3 1 4 0]\
minStack:   \[2 2 1 1 0]
{% endhint %}

```
class MinStack {

    Stack<Integer> stack;
    Stack<Integer> minStack;

    public MinStack() {
        stack = new Stack<>();
        minStack = new Stack();
    }
    
    public void push(int val) {
        stack.push(val);
        if (minStack.isEmpty() || val < minStack.peek()) {
            minStack.push(val);
        } else {
            minStack.push(minStack.peek());
        }
    }
    
    public void pop() {
        stack.pop();
        minStack.pop();
    }
    
    public int top() {
        return stack.peek();
    }
    
    public int getMin() {
       return minStack.peek();
    }
}
```
