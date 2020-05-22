```cpp
class Solution {
public:
    vector<string> restoreIpAddresses(string s) {
        vector<string> res;
        restore(s,0,res,4,"");
        return res;
    }
    void restore(string &s,int i,vector<string> &res,int k,string o){
        // k operator, o output, res answer, i string position
        int temp=0;
        int valid[3]={0,10,100};
        // cout<<o<<endl;
        if(k<4 && k>0)
            o+=".";
        if(k==0){
            if(i==s.size())
                res.push_back(o);
            return;
        }
            
        for(int j=0;j<3;j++){
            if(i+j==s.size()){
                break;
            }else{
                temp=10*temp+s[i+j]-'0';
                if(temp<=255 && temp>=valid[j]){
                    o+=s[i+j];
                    restore(s,i+j+1,res,k-1,o);
                }
                
            }

            
        }
        
        
    }
};
```