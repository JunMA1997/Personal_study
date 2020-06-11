```cpp
class Solution {
public:
    int evalRPN(vector<string>& tokens) {
        stack<int> s;
        int res=0;
        int a,b;
        // cout<<endl;
        for(int i=0;i<tokens.size();i++){
            if(tokens[i].size()==1 && tokens[i][0]<'0'){
                a=s.top();
                s.pop();
                b=s.top();
                s.pop();
                // cout<<a<<tokens[i][0]<<b;
                switch(tokens[i][0]){                        
                    case '+':
                        res=a+b;
                        break;
                    case '-':
                        res=(b-a);
                        break;
                    case '*':
                        res=(b*a);
                        break;
                    case '/':
                        res=(b/a);
                        break;
                }
                s.push(res);
                
            }else{
                s.push(stoi(tokens[i]));
            }
        }
        return s.top();
    }
};
```