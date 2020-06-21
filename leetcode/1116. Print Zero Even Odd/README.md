```cpp
class ZeroEvenOdd {
private:
    int n;
    mutex a,b,c;
    
public:
    ZeroEvenOdd(int n) {
        this->n = n;
        b.lock();
        c.lock();
    }

    // printNumber(x) outputs "x", where x is an integer.
    void zero(function<void(int)> printNumber) {
        for(int j=1;j<=n;j++){
            a.lock();
            int x=0;
            printNumber(x);
            if(j%2)
                c.unlock();
            else
                b.unlock();
        }
        

    }

    void even(function<void(int)> printNumber) {  
        for(int i=2;i<=n;i+=2){
            b.lock();
            printNumber(i);
            a.unlock();
        }
        
    }

    void odd(function<void(int)> printNumber) {
        for(int i=1;i<=n;i+=2){
            c.lock();       

            printNumber(i);

            a.unlock();
        }
        
    }
};
```