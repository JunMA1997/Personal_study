```cpp
class FizzBuzz {
private:
    int n;
    mutex f,b,fb,num;
public:
    FizzBuzz(int n) {
        this->n = n;
        f.lock();
        b.lock();
        fb.lock();
    }

    // printFizz() outputs "fizz".
    void fizz(function<void()> printFizz) {
        for(int i=0;i<(n/3-n/15);i++){
            f.lock();
            // cout<<"f";
            printFizz();
            num.unlock();
        }
    }

    // printBuzz() outputs "buzz".
    void buzz(function<void()> printBuzz) {
        for(int i=0;i<(n/5-n/15);i++){
            b.lock();
            // cout<<"b";
            printBuzz();
            num.unlock();
        }
    }

    // printFizzBuzz() outputs "fizzbuzz".
	void fizzbuzz(function<void()> printFizzBuzz) {
        for(int i=0;i<n/15;i++){
            fb.lock();
            // cout<<"fb";
            printFizzBuzz();
            num.unlock();
        }
    }

    // printNumber(x) outputs "x", where x is an integer.
    void number(function<void(int)> printNumber) {
        for(int i=1;i<=n;i++){
            if(i%5==0 && i%3==0){
                num.lock();                
                fb.unlock();
                
            }else{
                
                if(i%5==0){
                    num.lock();
                    b.unlock();
                }else if(i%3==0){
                    num.lock();
                    f.unlock();
                }else{
                    num.lock();
                    // cout<<i;
                    printNumber(i);
                    num.unlock();
                }
            }
        }
    }
};
```