```cpp
class Solution {
public:
    vector<vector<int>> combine(int n, int k) {
        vector<vector<int>> res;
        vector<int> cand(n),temp;
        for(int i=1;i<=n;i++)
            cand[i-1]=i;
        dfs(temp,cand,k,res,0);
        return res;
    }
    void dfs(vector<int> &temp,vector<int> &cand,int k, vector<vector<int>> &res,int now){
        if(k==0){
            res.push_back(temp);
            return;
        }
            
        
        for(int i=now;i<cand.size();i++){
            temp.push_back(cand[i]);
            dfs(temp,cand,k-1,res,i+1);
            temp.pop_back();
        }
    }
};
```