```cpp
class Solution {
public:
    vector<vector<int>> combinationSum3(int k, int n) {
        vector<vector<int>> res;
        vector<int> temp;
        int sum=0;
        helper(res,temp,k,n,sum,0);
        return res;
    }
    void helper(vector<vector<int>> &res,vector<int> &temp,int k,int n,int &sum,int i){
        if(temp.size()==k){
            if(sum==n)
                res.push_back(temp);
            return;
        }
        for(int j=i+1;j<10;j++){
            temp.push_back(j);
            sum+=j;
            helper(res,temp,k,n,sum,j);
            sum-=j;
            temp.pop_back();
        }
        
      
    }
};
```
# dfs