```cpp
class Solution {
public:
    bool isIsomorphic(string s, string t) {
        char map1[128],map2[128];
        memset(map1,0,sizeof(map1));
        memset(map2,0,sizeof(map2));
        if(s.size()!=t.size())
            return false;
        for(int i=0;i<s.size();i++){
            if(map1[s[i]]==0 && map2[t[i]]==0){
                map1[s[i]]=t[i];
                map2[t[i]]=s[i];
            }else if(map1[s[i]]!=t[i] || map2[t[i]]!=s[i]){
                return false;
            }
        }
        for(int i=0;i<128;i++);
        return true;
    }
};
```
# note: compare to two strings