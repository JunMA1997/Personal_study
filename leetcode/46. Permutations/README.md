```cpp
class Solution {
public:
    vector<vector<int>> permute(vector<int>& nums) {
        vector<vector<int>> res;
        fun(res,nums,0,nums.size()-1);
        return res;
    }
    void fun(vector<vector<int>> &res,vector<int>& nums,int l,int r){
        if(l==r){
            res.push_back(nums);
            return;
        }
        for(int i=l;i<=r;i++){
            swap(nums,l,i);
            fun(res,nums,l+1,r);
            swap(nums,l,i);
        }
    }
    void swap(vector<int>& nums,int i,int j){
        if(i==j)
            return;
        nums[i]=nums[i]+nums[j];
        nums[j]=nums[i]-nums[j];
        nums[i]=nums[i]-nums[j];
    }
};
```
# This solution using dfs
* l == r: lastest layers, push_back
* l < r: still have layers, Recursive, swap l and i, after exec, swap back