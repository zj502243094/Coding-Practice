# Implement Stack using Queues

[https://leetcode.com/problems/implement-stack-using-queues/](https://leetcode.com/problems/implement-stack-using-queues/)

{% hint style="info" %}
Stack is LIFO Queue is FIFO; 所以每次 用加到queue的末尾

\[1 2 3]  1 2 先后进入Q 之后 1 被弹出再加到 2 的后面 变成 \[2 1]

3 加入后 依次顺序是 \[2 1 3] 弹两次 \[1 3 2] \[3 2 1]&#x20;
{% endhint %}

```
class MyStack {
    
    Queue<Integer> queue = new LinkedList<Integer>();

    public MyStack() {
        
    }
    
    public void push(int x) {
        queue.add(x);
        for(int i = 1; i < queue.size(); i++){
            queue.add(queue.poll());
        }
    }
    
    public int pop() {
        return queue.poll();
    }
    
    public int top() {
        return queue.peek();
    }
    
    public boolean empty() {
        return queue.isEmpty();
    }
}
```
