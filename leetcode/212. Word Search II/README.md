```cpp
class Solution {
public:
    vector<string> findWords(vector<vector<char>>& board, vector<string>& words) {
        vector<string> res;
        for(int i=0;i<words.size();i++){
            if(exist(board,words[i])){
                res.push_back(words[i]);
            }
        }
        return res;
    }
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
# easy understand

```cpp
class Solution {
private:
    typedef struct Tree{
        char s;
        struct Tree *child[26];
        bool isEnd;
        Tree(char word){
            isEnd=false;
            s=word;
            memset(child,NULL,sizeof(child));
        }
    }Tree;
    Tree *root;
public:
    vector<string> findWords(vector<vector<char>>& board, vector<string>& words) {
        root=new Tree('1');
        if(board.size()==0)
            return {};
        if(board[0].size()==0)
            return {};
        for(int i=0;i<words.size();i++){
            if(words[i].size()<=board.size()*board[0].size()){
                insert(words[i]);
                // cout<<words[i]<<endl;
            }
                
        }
        unordered_set<string> c;
        vector<string> res;
        string temp;
        for(int z=0;z<26;z++){
            if(root->child[z]!=NULL){
                for(int i=0;i<board.size();i++){
                    for(int j=0;j<board[0].size();j++){
                        temp.push_back(root->child[z]->s);
                        helper(board,root->child[z],i,j,res,temp,c);
                        temp.pop_back();
                    }                        
                }
            }
        }
        return res;
    }
    void helper(vector<vector<char>>& board,Tree *iter,int i,int j,vector<string> &res,string &temp,unordered_set<string> &c){
        if(i<0 || i>=board.size() || j<0 || j>=board[0].size()){
            return;
        }
        
        if(iter->s==board[i][j]){
            
            for(int z=0;z<26;z++){
                if(iter->child[z]!=NULL){
                    temp.push_back(z+'a');
                    char t=board[i][j];
                    board[i][j]='.';
                    helper(board,iter->child[z],i+1,j,res,temp,c);
                    helper(board,iter->child[z],i-1,j,res,temp,c);
                    helper(board,iter->child[z],i,j+1,res,temp,c);
                    helper(board,iter->child[z],i,j-1,res,temp,c);
                    board[i][j]=t;
                    temp.pop_back();
                }
            }
            if(iter->isEnd==true){
                if(!c.count(temp))
                {
                    res.push_back(temp);
                    c.insert(temp);
                }                
                return;
            }
            
        }
        
    }
    void insert(string s){
        Tree *p=root;
        for(int i=0;i<s.size();i++){
            if(p->child[s[i]-'a']!=NULL){
                p=p->child[s[i]-'a'];
            }else{
                Tree *n=new Tree(s[i]);
                p->child[s[i]-'a']=n;
                p=n;
            }
        }
        p->isEnd=true;
    }
};
```
# use trie