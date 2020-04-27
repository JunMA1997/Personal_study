```cpp
class Solution {
public:
    bool isMatch(string s, string p) {
        if(p.empty())
            return s.empty();
        //empty pattern can only contains empty string
        bool dp[1+s.size()][1+p.size()];
        memset(dp,false, sizeof(dp));
        dp[0][0]=true;
        //0 pattern can match 0 string
        for(int i=1;i<=p.size();i++){
            if(p[i-1]=='*')
                dp[0][i]=dp[0][i-1];
        }
        //process *
        for(int i=1;i<=s.size();i++){
            for(int j=1;j<=p.size();j++){
                if(p[j-1]=='*'){
                    dp[i][j]=dp[i-1][j] || dp[i][j-1];                    
                }
                else
                    dp[i][j] = (s[i - 1] == p[j - 1] || p[j - 1] == '?') && dp[i - 1][j - 1];
            }
        }
        return dp[s.size()][p.size()];
    }
};
```
# using dp,48ms 69.32
* init matrix
* set [0,0] to true
* set [0,i] to [0,i-1] if p[i-1]="*"
* set [i,j] to [i-1,j] or [i,j-1] if p[j-1]=="*" , to ([i-1,j-1]) if s[i-1]=p[j-1] or p[j-1]=='?', to false in default.