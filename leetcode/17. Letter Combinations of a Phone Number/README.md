```cpp
class Solution {
public:
    vector<string> letterCombinations(string digits) {
        vector<string> res;
        string temp;
        dfs(digits,0,res,temp);
        return res;
    }
    void dfs(string &digits,int i,vector<string> &res,string &temp){
        if(i==digits.size() && i!=0){
            res.push_back(temp);
            return;
        }            
        else if(digits[i]=='2'){
            temp+="a";
            dfs(digits,i+1,res,temp);
            temp.pop_back();
            temp+="b";
            dfs(digits,i+1,res,temp);
            temp.pop_back();
            temp+="c";
            dfs(digits,i+1,res,temp);
            temp.pop_back();
        }
        else if(digits[i]=='3'){
            temp+="d";
            dfs(digits,i+1,res,temp);
            temp.pop_back();
            temp+="e";
            dfs(digits,i+1,res,temp);
            temp.pop_back();
            temp+="f";
            dfs(digits,i+1,res,temp);
            temp.pop_back();
        }
        else if(digits[i]=='4'){
            temp+="g";
            dfs(digits,i+1,res,temp);
            temp.pop_back();
            temp+="h";
            dfs(digits,i+1,res,temp);
            temp.pop_back();
            temp+="i";
            dfs(digits,i+1,res,temp);
            temp.pop_back();
        }
        else if(digits[i]=='5'){
            temp+="j";
            dfs(digits,i+1,res,temp);
            temp.pop_back();
            temp+="k";
            dfs(digits,i+1,res,temp);
            temp.pop_back();
            temp+="l";
            dfs(digits,i+1,res,temp);
            temp.pop_back();
        }
        else if(digits[i]=='6'){
            temp+="m";
            dfs(digits,i+1,res,temp);
            temp.pop_back();
            temp+="n";
            dfs(digits,i+1,res,temp);
            temp.pop_back();
            temp+="o";
            dfs(digits,i+1,res,temp);
            temp.pop_back();
        }
        else if(digits[i]=='7'){
            temp+="p";
            dfs(digits,i+1,res,temp);
            temp.pop_back();
            temp+="q";
            dfs(digits,i+1,res,temp);
            temp.pop_back();
            temp+="r";
            dfs(digits,i+1,res,temp);
            temp.pop_back();
            temp+="s";
            dfs(digits,i+1,res,temp);
            temp.pop_back();
        }
        else if(digits[i]=='8'){
            temp+="t";
            dfs(digits,i+1,res,temp);
            temp.pop_back();
            temp+="u";
            dfs(digits,i+1,res,temp);
            temp.pop_back();
            temp+="v";
            dfs(digits,i+1,res,temp);
            temp.pop_back();
        }
        else if(digits[i]=='9'){
            temp+="w";
            dfs(digits,i+1,res,temp);
            temp.pop_back();
            temp+="x";
            dfs(digits,i+1,res,temp);
            temp.pop_back();
            temp+="y";
            dfs(digits,i+1,res,temp);
            temp.pop_back();
            temp+="z";
            dfs(digits,i+1,res,temp);
            temp.pop_back();
        }
    }
};
```
