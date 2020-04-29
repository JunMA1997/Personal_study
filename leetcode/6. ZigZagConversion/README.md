```cpp
class Solution {
public:
    string convert(string s, int numRows) {
        string re="";
        int init;
        for(int i=0;i<numRows;i++)
        {            
            init=(numRows-i-1)*2;
            init=numRows==1?1:(numRows-1)*2-init;
            for(int pos=i;pos<s.size();pos=pos+init){               
                init=(init!=(numRows-1)*2 && init!=1)?(numRows-1)*2-init:init;
                re.push_back(s[pos]);
            }
                
        }
        return re;
    }
};
```
* still unknown why this is so slow.