![[Stack/Stack.excalidraw.md#^group=IpDTvAIwUMwuQ6m4ZmP3_|100%]]


## Using Two Queues
```cpp
class MyStack {
public:
    queue<int> Q1;
    queue<int> Q2;
    MyStack() {
    }
    
    void push(int x) {
        Q2.push(x);
        while(!Q1.empty()){
            Q2.push(Q1.front());
            Q1.pop();
        }
        swap(Q1,Q2);
    }
    
    int pop() {
        int x = Q1.front();
        Q1.pop();
        return x;
    }
    
    int top() {
        return Q1.front();
    }
    
    bool empty() {
        return Q1.empty();
    }
};

/**
 * Your MyStack object will be instantiated and called as such:
 * MyStack* obj = new MyStack();
 * obj->push(x);
 * int param_2 = obj->pop();
 * int param_3 = obj->top();
 * bool param_4 = obj->empty();
 */

```

## Using Single Queue 
```cpp
class MyStack {
public:
    queue<int> Q;
    MyStack() {
    }
    
    void push(int x) {
        int s = this->Q.size();
        Q.push(x);
        for (int i=0; i<s; i++) {
            int f = this->Q.front();
            Q.pop();
            Q.push(f);
        }
    }
    
    int pop() {
        int x = this->Q.front();
        Q.pop();
        return x;
    }
    
    int top() {
        return this->Q.front();
    }
    
    bool empty() {
        return this->Q.empty();
    }
};

/**
 * Your MyStack object will be instantiated and called as such:
 * MyStack* obj = new MyStack();
 * obj->push(x);
 * int param_2 = obj->pop();
 * int param_3 = obj->top();
 * bool param_4 = obj->empty();
 */

```

