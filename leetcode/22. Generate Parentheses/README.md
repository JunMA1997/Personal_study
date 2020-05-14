```cpp
class Solution {
public:
    void generate(int open,int close,int n,string &temp,vector<string> &res){
        if(temp.size()==n*2){
            res.push_back(temp);
            return;
        }            
        if(open<n){
            temp+="(";
            generate(open+1,close,n,temp,res);
            temp.pop_back();
        }
        if(close<open){
            temp+=")";
            generate(open,close+1,n,temp,res);
            temp.pop_back();
        }
    }
    vector<string> generateParenthesis(int n) {
        vector<string> res;
        string temp;
        generate(0,0,n,temp,res);
        return res;
    }
};
```
# this solution use less memory