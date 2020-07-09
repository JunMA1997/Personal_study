```cpp
class Solution {
public:
    int calculate(string s) {
        stack<int> nums;
        int res=0,num=0;
        char op='+';
        for(int i=0;i<s.size();i++){
            if(s[i]>='0'){
                num=num*10+(s[i]-'0');                
            }
            if((s[i]!=' ' && s[i]<'0') || i==s.size()-1){
                if(op=='+')
                    nums.push(num);
                else if(op=='-')
                    nums.push(-num);
                else{
                    int tmp=(op=='*')?nums.top()*num:nums.top()/num;
                    // cout<<tmp<<endl;
                    nums.pop();
                    nums.push(tmp);                    
                }
                op=s[i];
                num=0;
            }
            
        }
        while(nums.size()){
            // cout<<nums.top()<<" ";
            res+=nums.top();
            nums.pop();
        }
        return res;
    }
};
```