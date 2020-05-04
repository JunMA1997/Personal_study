```cpp
class Solution {
public:
    vector<vector<int>> generateMatrix(int n) {
        vector<vector<int>> res(n,vector<int>(n));
        int op=0;
        int col=0,row=0;
        for(int i=0;i<n*n;i++){ 
            // cout<<op<<row<<col<<i+1<<endl;
            if(op%4==0){
                
                res[row][col++]=i+1;            
                if(col+op/4==n){
                    col--;
                    row++;                    
                    op++; 
                }   
            }else if(op%4==1){
                
                res[row++][col]=i+1;
                if(row+op/4==n){
                    col--;
                    row--;
                    op++; 
                }
            }else if(op%4==2){
                
                res[row][col--]=i+1;
                if(col==op/4-1){
                    row--;
                    col++;
                    op++; 
                }
                
            }else if(op%4==3){
                
                res[row--][col]=i+1;
                if(row==op/4){
                    col++;
                    row++;
                    op++; 
                }
            }
            
        }
        return res;
    }
};
```
# easy solution