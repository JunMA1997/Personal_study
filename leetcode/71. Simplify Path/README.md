```cpp
class Solution {
public:
    string simplifyPath(string path) {
        vector<string> contents;
        string temp;
        for(int i=0;i<path.size();i++){
            
            if(path[i]=='/' || i==path.size()-1){
                if(path[i]!='/')
                    temp+=path[i];
                if(temp.size()!=0){
                    if(temp[0]=='.'){
                        if(temp.size()==1){
                            
                            temp="";
                            continue;
                        }
                        else if(temp.size()==2){
                           if(contents.size()>=1)
                                contents.pop_back();  
                        }   
                        else{
                            contents.push_back(temp);
                        }
                    }else{
                        contents.push_back(temp);
                    }
                }
                temp="";
            }
            else
                temp+=path[i];            
        }
        temp="";
        for(int i=0;i<contents.size();i++)
            temp+="/"+contents[i];
        if(temp.size()==0)
            return "/";
        return temp;
    }
};
```
# easy solution