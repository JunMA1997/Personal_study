```cpp
class Solution {
public:
    int numTrees(int n) {
        vector<int> dp(n+1);
        dp[0]=dp[1]=1;
        for(int i=2;i<=n;i++){
            for(int j=0;j<i;j++)
                dp[i]+=dp[j]*dp[i-j-1];
        }
        return dp[n];
    }
};
```
# 卡塔兰数 Catalan Number
* $ C_0=1 $
* $ C_{n+1}=\sum_{i=0}^{n}C_iC{n-i} $
