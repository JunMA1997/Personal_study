```cpp
class Solution {
public:
    bool isHappy(int n) {
        unordered_set<int> s;
        while(1){
            if(!s.count(n))
                s.insert(n);
            else if(n!=1)
                return false;
            else return true;
            int i=n;
            n=0;
            while(i){
                n+=(i%10)*(i%10);
                i/=10;
            }
        }
        return false;
    }
};
```