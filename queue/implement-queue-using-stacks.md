# Implement Queue using Stacks

[https://leetcode.com/problems/implement-queue-using-stacks/](https://leetcode.com/problems/implement-queue-using-stacks/)

> Implement a first in first out (FIFO) queue using only two stacks. The implemented queue should support all the functions of a normal queue (`push`, `peek`, `pop`, and `empty`).
>
> Implement the `MyQueue` class:
>
> * `void push(int x)` Pushes element x to the back of the queue.
> * `int pop()` Removes the element from the front of the queue and returns it.
> * `int peek()` Returns the element at the front of the queue.
> * `boolean empty()` Returns `true` if the queue is empty, `false` otherwise.
>
> **Example 1:**
>
> ```
> Input
> ["MyQueue", "push", "push", "peek", "pop", "empty"]
> [[], [1], [2], [], [], []]
> Output
> [null, null, null, 1, 1, false]
>
> Explanation
> MyQueue myQueue = new MyQueue();
> myQueue.push(1); // queue is: [1]
> myQueue.push(2); // queue is: [1, 2] (leftmost is front of the queue)
> myQueue.peek(); // return 1
> myQueue.pop(); // return 1, queue is [2]
> myQueue.empty(); // return false
> ```

{% hint style="info" %}
Queue 是FIFO Stack 是LIFO 所以push是向S1 弹出的时候 用S2弹\
\
比如 \[1 2 3] push 到 S1 \[1 2 3]  \
从S1出来pop到S2就是\[3 2 1]&#x20;

从S2弹出来就是 \[1 2 3]    实现了队列的先入先出
{% endhint %}

```
class MyQueue {
    
    Stack<Integer> s1 = new Stack();
    Stack<Integer> s2 = new Stack();

    public MyQueue() {
        s1 = new Stack<>();
        s2 = new Stack<>();
    }
    
    public void push(int x) {
        s1.push(x);
    }
    
    public int pop() {
        if (s2.isEmpty()) {
            while (!s1.isEmpty()) {
                s2.push(s1.pop());
            }
        }
        return s2.pop();
    }
    
    public int peek() {
        if (s2.isEmpty()) {
            while (!s1.isEmpty()) {
                s2.push(s1.pop());
            }
        }
        return s2.peek();
    }
    
    public boolean empty() {
        return s1.isEmpty() && s2.isEmpty();
    }
}
```
