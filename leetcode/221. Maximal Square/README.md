```cpp
class Solution {
public:
    int maximalSquare(vector<vector<char>>& matrix) {
        if(matrix.size()==0)
            return 0;
        vector<vector<int>> dp(matrix.size(),vector<int> (matrix[0].size(),0));
        int re=0;
        for(int i=0;i<matrix.size();i++){
            for(int j=0;j<matrix[0].size();j++){
                if(matrix[i][j]=='1'){
                    int mintemp=1;
                    if(i!=0&&j!=0){
                        mintemp=min(min(dp[i][j-1],dp[i-1][j]),dp[i-1][j-1])+1;
                    }
                    dp[i][j]=mintemp;
                    re=max(re,dp[i][j]);
                }
            }
        }
        return re*re;
        

            
    }
};
```