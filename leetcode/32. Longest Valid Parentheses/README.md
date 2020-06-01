```cpp
class Solution {
public:
    int longestValidParentheses(string s) {
        vector<int> mark;
        int now=0,max=0,temp=0;
        for(int i=0;i<s.size();i++){
            if(s[i]=='('){
                temp++;
                mark.push_back(now);
                now=0;
            }else{
                if(temp!=0){
                    now+=mark[mark.size()-1];
                    now+=2;
                    if(now>max){
                        max=now;
                    }
                    temp--;
                    mark.pop_back();
                }else{
                    now=0;
                    continue;
                }
            }
        }
        if(mark.size()>0 && mark[mark.size()-1]>max){
            return mark[mark.size()-1];
        }
        return max;
    }
};
```