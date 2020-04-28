```cpp
class Solution {
public:
    string longestPalindrome(string s) {
        if(s.size()<=1)
            return s;
        int longest=0,ll;
        for(int i=0;i<s.size();i++){
            int len1=substring(s,i,0);
            int len2=substring(s,i,1);
            int len=max(len1,len2);
            if(len>=longest){
                longest=len;
                ll=i-(len)/2;
            }
        }
        return s.substr(ll,longest+1);
    }
    int substring(string &s,int cen,int type){
        int l=cen,r=cen;
        if(type==1)
            r+=1;
        while(l>=0 && r<s.size()){
            if(s[l]!=s[r])
                break;
            l--;
            r++;
        }
        return (--r)-(++l);
    }
};
```
# this solution is O($n^2$)
* from center to find a substring
* using & to decrease memory usage.

