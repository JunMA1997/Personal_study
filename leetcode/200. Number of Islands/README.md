```cpp
class Solution {
public:
    int numIslands(vector<vector<char>>& grid) {
        if(grid.size()==0 || grid[0].size()==0)
            return 0;
        
        vector<vector<bool>> visit(grid.size(),vector<bool>(grid[0].size(),false));
        int res=0;
        for(int i=0;i<grid.size();i++){
            for(int j=0;j<grid[0].size();j++){
                
                
                if(visit[i][j] || grid[i][j]=='0'){
                    continue;
                }
                    
                discover(grid,i,j,visit);
                // for(int i1=0;i1<grid.size();i1++){
                //     for(int j1=0;j1<grid[0].size();j1++){
                //         cout<<visit[i1][j1];
                //     }
                //     cout<<endl;
                // }
                // cout<<endl;
                res++;
            }
           
        }
        return res;
    }
    void discover(vector<vector<char>>& grid,int i,int j,vector<vector<bool>> &visit){
 
        if(grid[i][j]=='0'|| visit[i][j]){           
            return;
        }
        visit[i][j]=true;
        if(i-1>-1)
            discover(grid,i-1,j,visit);
        if(i+1<grid.size())
            discover(grid,i+1,j,visit);
        if(j-1>-1)
            discover(grid,i,j-1,visit);
        if(j+1<grid[0].size())
            discover(grid,i,j+1,visit);
    }
};
```