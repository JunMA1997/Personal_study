```cpp
class Solution {
public:
    string multiply(string num1, string num2) {
        
        string res="";
        int m = num1.size(),n = num2.size();
        vector<int> vals(m+n);
        for(int i = m-1; i >= 0; i--){
            for(int j = n-1; j >= 0; j--){
                int sum=(num1[i]-'0')*(num2[j]-'0')+vals[i+j+1];
                vals[i+j]+=sum/10;
                vals[i+j+1]=sum%10;
            }
        }
        for(int val : vals){
            if(val!=0 || !res.empty())
                res+=(val+'0');
        }
        return res.empty() ? "0":res;
    }
};
```
# REF:https://www.cnblogs.com/grandyang/p/4395356.html
* NOTE: high position first. 64.99
* if nums1.size()=m, nums2.size()=n then results.size()<=m+n
* need addc judge