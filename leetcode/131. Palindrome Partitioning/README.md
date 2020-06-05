```cpp
class Solution {
public:
    vector<vector<string>> partition(string s) {
        if(s.size()<=0)
            return {};
        vector<vector<string>> res;
        vector<string> temp;
        helper(s,res,temp,0,"");
        return res;
    }
    void helper(string s,vector<vector<string>> &res,vector<string> &temp,int pos,string t){
        if(pos==s.size()){
            res.push_back(temp);
            return;
        }
            
        for(int i=pos;i<s.size();i++){
            t+=s[i];
            if(isPa(t)){
                temp.push_back(t);
                helper(s,res,temp,i+1,"");
                temp.pop_back();
            }
        }
    }
    bool isPa(string s){
        for(int i=0;i<s.size()/2;i++){
            if(s[i]!=s[s.size()-1-i])
                return false;
        }
        return true;
    }
};
```