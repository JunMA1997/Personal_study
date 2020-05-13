```cpp
class Solution {
public:
    vector<vector<int>> subsets(vector<int>& nums) {
        vector<vector<int>> res;  
        vector<int> temp;
        test(res,temp,nums,0);
        return res;
    }
    void test(vector<vector<int>> &res,vector<int>& temp,vector<int>& nums,int k){
        res.push_back(temp);
        for(int i=k;i<nums.size();i++){
            temp.push_back(nums[i]);
            test(res,temp,nums,i+1);
            temp.pop_back();
        }
    }
};
```
# solution with dfs, save all route(idk this answer is correct)