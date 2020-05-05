```cpp
class Solution {
public:
    string getPermutation(int n, int k) {
        string num="123456789";
        string res="";
        int i,a=1;
        for(i=1;i<=n;i++){
            a*=i;
        }         
        a/=n;
        k--;

        for(i=0;n>1;n--,i++,a/=n){
            
            int j=k/a;
            k%=a;
            // cout<<num[j]<<" "<<j<<res<<endl;
            res.push_back(num[j]);
            num.erase(j,1);            
        }
        res.push_back(num[0]);
        return res;
    }
};
```
# using num to enum all possible num
