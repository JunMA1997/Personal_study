```CPP
class Solution {
public:
    vector<vector<int>> permuteUnique(vector<int>& nums) {
        vector<vector<int>> res;
        dfs(res,nums,0,nums.size());
        // sort(res.begin(),res.end());
        // res.erase(unique(res.begin(),res.end()),res.end());
        return res;
    }
    void dfs(vector<vector<int>> &res,vector<int>& nums,int l,int r){        
        if(l==r){
            res.push_back(nums);
            return;
        }
        vector<int> t;
        for(int i=l;i<r;i++){
            if(check(i,nums,t))
                continue;
            t.push_back(nums[i]);
            swap(nums,l,i);
            dfs(res,nums,l+1,r);
            swap(nums,l,i);            
        }
    }
    void swap(vector<int>& nums,int l,int r){
        if(l==r){
            return;
        }
        nums[l]=nums[l]+nums[r];
        nums[r]=nums[l]-nums[r];
        nums[l]=nums[l]-nums[r];
    }
    bool check(int i,vector<int>& nums,vector<int>& t){
        bool flag=false;
        for(int j=0;j<t.size();j++){
            if(t[j]==nums[i])
            {
                return true;
            }
        }
        return false;
    }
};
```
* same like 46, need to check duplicate