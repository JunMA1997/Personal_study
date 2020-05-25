```cpp
class Solution {
public:
    int numDecodings(string s) {
        if(s[0]=='0')
            return 0;
        vector<int> res(s.size()+1,0);
        res[0]=1;
        for(int i=1;i<res.size();i++){
            res[i]=s[i-1]=='0'?0:res[i-1];
            if(i>1 && ((s[i-1]<='6' && s[i-2]=='2') || s[i-2]=='1')){
                // cout<<1;
                res[i]+=res[i-2];
            }
        }
        return res[res.size()-1];
    }
};
```
# using dp,
* dp[i]=(s[i-1]=='0'?0:dp[i-1]) + ((i>1 && ((s[i-1]<='6' && s[i-2]=='2') || s[i-2]=='1')?0:dp[i-2]);