```cpp
class Solution {
public:
    int myAtoi(string str) {
        bool flag=false,flag2=false,flag3=false;
        long long res=0;
        for(int i=0;i<str.size();i++){
            if(str[i]==' ' && !flag)
                continue;
            else if(str[i]<='9' && str[i]>='0'){
                flag=1;
                flag2=1;
                
                res*=10;
                if(res> INT_MAX)
                    break;
                res+=str[i]-'0';
            }else if(str[i]=='-' && !flag2){
                flag=1;
                flag3=1;
                flag2=1;
            }else if(str[i]=='+' && !flag2){
                flag2=1;
                flag=1;
            }else
                break;
        }
        if(flag3)
            res*=-1;
        if(res<INT_MIN)
            return INT_MIN;
        if(res>INT_MAX)
            return INT_MAX;
        return res;
    }
};
```
# easy solution
* need to note edge case