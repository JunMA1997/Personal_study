```cpp
class Solution {
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        vector<int> res;
        int m=matrix.size();
        if(m<=0)
            return res;
        int n=matrix[0].size();
        if(n<=0)
            return res;
        int num=m*n;
        int op=1;
        res=matrix[0];
        int row=0,col=n-1;
        for(int i=0;i<num-n;i++){            
            if((op)%4==1){
                // ++row;
                //down
                res.emplace_back(matrix[++row][col]);
                if(row+(op/4)==m-1)
                    op++;
            }
            else if((op)%4==2){
                // --col;
                //left
                res.emplace_back(matrix[row][--col]);
                if(col-(op/4)==0)
                    op++;
            }
            else if((op)%4==3){
                // --row;
                //up
                res.emplace_back(matrix[--row][col]);
                if(row==1+(op/4))
                    op++;
            }else{
                // ++col;
                //right
                res.emplace_back(matrix[row][++col]);
                if(col+(op/4)==n-1)
                    op++;
            }
            // for(int z=0;z<res.size();z++)
            //     cout<<res[z];
            // cout<<" "<<row<<col<<endl;
        }
        return res;
    }
};
```
# easy solution