## **155. Min Stack**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/04/2023 18:30	| 	18 ms | 16.3 MB	 | Accepted |

```
class MinStack {
public:
    struct INT2 {
        int val;
        int min;
    };
    stack<INT2> minstack;
    MinStack() {
        while(!minstack.empty()) {
            minstack.pop();
        }
    }
    
    void push(int val) {
        int min;
        if (minstack.empty()) min = val;
        else {
            min = minstack.top().min;
            if (val < min)  min = val;
        }
        
        minstack.push({val=val, min=min});
    }
    
    void pop() {
        minstack.pop();
    }
    
    int top() {
        return minstack.top().val;
    }
    
    int getMin() {
        return minstack.top().min;
    }
};

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack* obj = new MinStack();
 * obj->push(val);
 * obj->pop();
 * int param_3 = obj->top();
 * int param_4 = obj->getMin();
 */
```

