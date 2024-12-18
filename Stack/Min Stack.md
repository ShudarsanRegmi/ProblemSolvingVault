


![[Stack/Stack.excalidraw.md#^group=b9OBHpkLc6QTGW1N1TiDm|100%]]


### Using Two Stacks

```cpp
class MinStack {
public:
    stack<int> st;
    stack<int> mst;
    MinStack() {}
    
    void push(int val) {
        if (st.empty() || val < mst.top()) {
            mst.push(val);
        }else{
            mst.push(mst.top());
        }
        st.push(val);
    }
    
    void pop() {
        st.pop();
        mst.pop();
    }
    
    int top() {
        return st.top();
    }
    
    int getMin() {
        return mst.top();
    }
};

```


![[Stack/Stack.excalidraw.md#^group=MvHtgJUNTRbWSqAsVfyWN|100%]]

## Using single stack

```cpp

```

 I couldn't write code for it..
 