```cpp
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        string res="";
        int flag=0;
        if(strs.size()==0)
            return res;
        for(int i=0;i<strs[0].size();i++){
            for(int j=0;j<strs.size();j++){
                if(strs[j][i]!=strs[0][i]){
                    flag=1;
                    break;
                }
            }
            if(flag)
                break;
            res+=strs[0][i];
        }
        return res;
    }
};
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        int j,i;
        int flag=0;
        if(strs.size()==0)
            return "";
        for(i=0;i<strs[0].size();i++){
            for(j=0;j<strs.size();j++){
                if(strs[j][i]!=strs[0][i]){
                    flag=1;
                    break;
                }
            }
            if(flag)
                break;

        }
       
        return strs[0].substr(0,i);
    }
};
```
# easy solution