```cpp
class MyStack {
private:
    queue<int> stack;
public:
    /** Initialize your data structure here. */
    MyStack() {
        
    }
    
    /** Push element x onto stack. */
    void push(int x) {
        queue<int> temp;
        swap(stack,temp);
        stack.push(x);
        while(temp.size()){
            stack.push(temp.front());
            temp.pop();
        }
    }
    
    /** Removes the element on top of the stack and returns that element. */
    int pop() {
        int re=stack.front();
        stack.pop();
        return re;
    }
    
    /** Get the top element. */
    int top() {
        return stack.front();
    }
    
    /** Returns whether the stack is empty. */
    bool empty() {
        // cout<<stack.size();
        // if(stack.size())
        //     return true;
        // return false;
        return !stack.size();
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