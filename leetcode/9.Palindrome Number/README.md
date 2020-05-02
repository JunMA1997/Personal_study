```cpp
class Solution {
public:
    bool isPalindrome(int x) {
        if(x<0)
            return false;
        int a=x;
        long res=0;
        while(a!=0){
            if(res>INT_MAX)
                return false;
            res*=10;
            res+=a%10;
            a/=10;
        }
        return x==res;
    }
};
```