```cpp
class Solution {
public:
    bool exist(vector<vector<char>>& board, string word) {
        
        if(word.size()<=0)
            return true;
        if(board.size()<=0)
            return false;
        vector<vector<bool>> check(board.size(),vector<bool>(board[0].size(),0));
        for(int i=0;i<board.size();i++){
            for(int j=0;j<board[i].size();j++){
                if(search(board,check,i,j,0,word))
                    return true;
            }
        }
        return false;
    }
    bool search(vector<vector<char>>& board,vector<vector<bool>>& check,int i,int j,int k,string &word){
        
        if(k==word.size())
            return true;
        if(i<0 || i>=board.size() || j<0 || j>=board[0].size()){
            return false;
        }
        if(check[i][j]==1)
            return false;
        if(word[k]!=board[i][j])
            return false;
        bool re;
        // if(k>850)
        //     cout<<k<<endl;
        check[i][j]=1;
        re=search(board,check,i-1,j,k+1,word) || search(board,check,i,j-1,k+1,word) || search(board,check,i+1,j,k+1,word) || search(board,check,i,j+1,k+1,word);
        check[i][j]=0;
        return re;
        
    }
};
```
# using dfs, 

```cpp
class Solution {
public:
    bool exist(vector<vector<char>>& board, string word) {
        
        if(word.size()<=0)
            return true;
        if(board.size()<=0)
            return false;
        
        // vector<vector<bool>> check(board.size(),vector<bool>(board[0].size(),0));
        for(int i=0;i<board.size();i++){
            for(int j=0;j<board[i].size();j++){
                if(search(board,i,j,0,word))
                    return true;
            }
        }
        return false;
    }
    bool search(vector<vector<char>>& board,int i,int j,int k,string &word){
        char temp;
        if(k==word.size())
            return true;
        if(i<0 || i>=board.size() || j<0 || j>=board[0].size()){
            return false;
        }
        if(word[k]!=board[i][j])
            return false;
        bool re;
        // if(k>850)
        //     cout<<k<<endl;
        temp=board[i][j];
        board[i][j]=0;
        re=search(board,i-1,j,k+1,word) || search(board,i,j-1,k+1,word) || search(board,i+1,j,k+1,word) || search(board,i,j+1,k+1,word);
        board[i][j]=temp;
        return re;
        
    }
};
```
# using board itself to mark used.