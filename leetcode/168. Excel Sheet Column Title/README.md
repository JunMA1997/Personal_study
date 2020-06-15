```cpp
class Solution {
public:
    string convertToTitle(int n) {
        string res;
        while(n){
            char a=(n-1)%26+'A';
            res=a+res;
            n=(n-1)/26;
        }
        return res;
    }
};
```