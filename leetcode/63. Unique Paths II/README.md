```cpp
class Solution {
public:
    int uniquePathsWithObstacles(vector<vector<int>>& obstacleGrid) {
        int m=obstacleGrid.size();
        if(m<=0)
            return 0;
        int n=obstacleGrid[0].size();
        if(n<=0)
            return 0;
        vector<int> dp(n,0);
        if(obstacleGrid[0][0]==1 || obstacleGrid[m-1][n-1]==1)
            return 0;
        dp[0]=1;
        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                
                    
                if(obstacleGrid[i][j]==1){
                    dp[j]=0;
                }else{
                    if(j==0){
                        continue;
                    }
                    dp[j]+=dp[j-1];
                }
                // cout<<dp[j]<<" ";
            }
            // cout<<endl;
        }
        return dp[n-1];
    }
};
```
# same solution with 62 unique paths, 
add 
```cpp
if(obstacleGrid[i][j]==1){
    dp[j]=0;
}
```