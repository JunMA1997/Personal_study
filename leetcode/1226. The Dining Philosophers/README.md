```cpp
class DiningPhilosophers {
private:
    mutex forklock[5];
public:
    DiningPhilosophers() {
        
    }

    void wantsToEat(int philosopher,
                    function<void()> pickLeftFork,
                    function<void()> pickRightFork,
                    function<void()> eat,
                    function<void()> putLeftFork,
                    function<void()> putRightFork) {
		int leftfork=philosopher,rightfork=(philosopher+1)%5;
        if(philosopher%2==0){
            forklock[leftfork].lock();
            forklock[rightfork].lock();
        }else{
            forklock[rightfork].lock();
            forklock[leftfork].lock();            
        }        
        pickLeftFork();        
        pickRightFork();
        eat();
        putRightFork();
        forklock[rightfork].unlock();
        putLeftFork();
        forklock[leftfork].unlock();
        
        
    }
};
```
# notice:
* odd philosopher need to snatch left and even snatch right first in order to avoid dead lock