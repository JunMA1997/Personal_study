```cpp
class Solution {
public:
    int compareVersion(string version1, string version2) {
        vector<int> v1,v2;
        int last=0;
 
        for(int i=0;i<version1.size();i++){
            if(version1[i]=='.' || i==version1.size()-1){
                
                v1.push_back(stoi(version1.substr(last,i-last+1)));
                last=i+1;
            }
        }
        
        last=0;
        for(int i=0;i<version2.size();i++){
            if(version2[i]=='.'|| i==version2.size()-1){
                v2.push_back(stoi(version2.substr(last,i-last+1)));
                last=i+1;
            }
        }
        // for(int i=0;i<v1.size();i++)
        //     cout<<v1[i];
        // cout<<endl;
        // for(int i=0;i<v2.size();i++)
        //     cout<<v2[i];
        int i=0;
        for(;i<v1.size();i++){
            if(i>=v2.size()){
                for(;i<v1.size();i++){
                    if(v1[i]!=0)
                        return 1;
                }
                return 0;
            }                
            if(v1[i]>v2[i])
                return 1;
            if(v1[i]<v2[i])
                return -1;
        }
        for(;i<v2.size();i++){
            if(v2[i]!=0)
                return -1;
        }
        return 0;
    }
};
```