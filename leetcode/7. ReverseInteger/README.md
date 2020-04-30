```cpp
class Solution {
public:
    int reverse(int x) {
        long long res=0;
        while(x!=0){
            res*=10;
            res+=x%10;
            x/=10;
        }
        if(res>=INT_MAX or res<=INT_MIN)
            res=0;
        return res;
    }
};
```
# easy solution