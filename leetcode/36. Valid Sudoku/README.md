```cpp
class Solution {
public:
    bool isValidSudoku(vector<vector<char>>& board) {
        unordered_set<char> a;
        unordered_set<char> b;
        unordered_set<char> c;
        int x,y;
        for(int i=0;i<9;i++){
            a.clear();
            b.clear();
            c.clear();
            for(int j=0;j<9;j++){
                // board[i][j]->a
                // board[j][i]->b
                if(board[i][j]!='.'){
                    if(a.count(board[i][j])){
                        // cout<<i<<j<<"恒";
                        return false;
                    }
                        
                    else
                        a.insert(board[i][j]);
                }
                if(board[j][i]!='.'){
                    if(b.count(board[j][i])){
                        // cout<<i<<j<<"纵";
                        return false;
                    }
                    else
                        b.insert(board[j][i]);
                }
            }

            for(x=i%3*3;x<i%3*3+3;x++){
                for(y=(i/3)*3;y<(i/3)*3+3;y++){
                    if(board[x][y]!='.'){
                        if(c.count(board[x][y])){
                            // cout<<x<<y<<i<<"xy";
                            return false;
                        }
                            
                        else
                            c.insert(board[x][y]);
                    }
                }
            }
        }
        
        return true;
        
    }
};
```