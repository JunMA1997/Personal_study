```cpp
class H2O {
private:
    mutex H,O;
    int HNums;
public:
    H2O() {
        HNums=0;
    }

    void hydrogen(function<void()> releaseHydrogen) {
        H.lock();
        // releaseHydrogen() outputs "H". Do not change or remove this line.
        releaseHydrogen();
        
        if(++HNums==2){
            HNums=0;
            O.unlock();
        }else{
            H.unlock();
        }
    }

    void oxygen(function<void()> releaseOxygen) {
        O.lock();
        // releaseOxygen() outputs "O". Do not change or remove this line.
        releaseOxygen();
        H.unlock();
    }
};
```