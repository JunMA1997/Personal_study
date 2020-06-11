```cpp
class Solution {
public:
    string reverseWords(string s) {
        // if(s.size()<=0)
        //     return s;
        char temp;
        for(int i=0;i<s.size()/2;i++){
            temp=s[i];
            s[i]=s[s.size()-1-i];
            s[s.size()-1-i]=temp;
        }
        int i=0;
        while(s.size()>0){
            if(s[0]==' ')
                s.erase(0,1); 
            else{
                if(s[s.size()-1]==' ')
                    s.erase(s.size()-1,1);
                else
                    break;
            }
        }
        for(i=1;i<s.size();i++){
            if(s[i-1]==' ' && s[i]==' '){
                s.erase(i,1);
                i--;
            }
                
        }
        cout<<s;
        int last=0;
        for(i=0;i<s.size();i++){
            if(s[i]==' '){
                // cout<<i<<last<<(i+last)/2<<endl;
                for(int j=0;j<(i-last)/2;j++){
                    temp=s[j+last];
                    s[j+last]=s[i-1-j];
                    s[i-1-j]=temp;
                }
                last=i+1;
            }
        }
        if(s.size()<=0)
            return s;
        for(int j=0;j<(s.size()-last)/2;j++){
            temp=s[j+last];
            s[j+last]=s[i-1-j];
            s[i-1-j]=temp;
        }
           
        return s;
    }
};
```
# use constant space and O(n) complex i think
* reverse all string
* remove redundant space
* reverse all words