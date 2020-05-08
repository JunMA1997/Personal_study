```cpp
class Solution {
public:
    int minPathSum(vector<vector<int>>& grid) {
        if(grid.size()<=0)
            return 0;
        if(grid[0].size()<=0)
            return 0;
        for(int i=0;i<grid.size();i++){
            for(int j=0;j<grid[0].size();j++){
                if(i==0 && j==0)
                    continue;
                if(i==0){
                    grid[i][j]+=grid[i][j-1];
                    continue;
                }
                if(j==0){
                    grid[i][j]+=grid[i-1][j];
                    continue;
                }
                grid[i][j]+=min(grid[i-1][j],grid[i][j-1]);
            }
        }
        return grid[grid.size()-1][grid[0].size()-1];
    }
};
```
# same with 62, add weight to grid.