```cpp
class Solution {
public:
    bool isValid(string s) {
        vector<char> temp;
        for(int i=0;i<s.size();i++){
            // for(int j=0;j<temp.size();j++)
            //     cout<<temp[j];
            // cout<<endl;
            if(s[i]=='(' || s[i]=='{' || s[i]=='['){
                temp.push_back(s[i]);
            }else{
                if(temp.size()<=0)
                    return false;
                if(s[i]==')'){
                    if(temp[temp.size()-1]=='(')
                        temp.pop_back();
                    else 
                        return false;
                }else if(s[i]==']'){
                    if(temp[temp.size()-1]=='[')
                        temp.pop_back();
                    else 
                        return false;
                }else if(s[i]=='}'){
                    if(temp[temp.size()-1]=='{')
                        temp.pop_back();
                    
                    else 
                        return false;
                }
            }
        }
        if(temp.size()==0)
            return true;
        return false;
    }
    
};
```