```cpp
class Solution {
public:
    void helper(vector<vector<char>>& board,int i,int j,vector<vector<bool>> &b,vector<vector<bool>> &check,int &m,int &n){
        if(board[i][j]=='X')
            return;
        b[i][j]=false;
        check[i][j]=true;
        if(i+1<m-1 && !check[i+1][j])
            helper(board,i+1,j,b,check,m,n);
        if(i-1>0 && !check[i-1][j])
            helper(board,i-1,j,b,check,m,n);
        if(j+1<n-1 && !check[i][j+1])
            helper(board,i,j+1,b,check,m,n);
        if(j-1>0 && !check[i][j-1])
            helper(board,i,j-1,b,check,m,n);
    }
    void solve(vector<vector<char>>& board) {
        if(board.size()<=2)
            return;
        if(board[0].size()<=2)
            return;
        int m=board.size();
        int n=board[0].size();
        vector<vector<bool>> b(board.size(),vector<bool>(board[0].size(),true));
        vector<vector<bool>> check(board.size(),vector<bool>(board[0].size(),false));
        for(int i=0;i<board.size();i++){
            check[i][0]=true;
            check[i][board[i].size()-1]=true;
            if(board[i][0]=='O')
                helper(board,i,1,b,check,m,n);                
            if(board[i][board[i].size()-1]=='O')
                helper(board,i,board[i].size()-2,b,check,m,n);           
        }
        for(int i=0;i<board[0].size();i++){
            check[0][i]=true;
            check[board.size()-1][i]=true;
            if(board[0][i]=='O')
                helper(board,1,i,b,check,m,n);
            if(board[board.size()-1][i]=='O')
                helper(board,board.size()-2,i,b,check,m,n);         
        }
        for(int i=1;i<m-1;i++){
            for(int j=1;j<n-1;j++){
                if(board[i][j]=='O' && b[i][j])
                    board[i][j]='X';
            }
            
        }
    }
};
```