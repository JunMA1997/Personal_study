```cpp
class Solution {
public:
    vector<vector<int>> fourSum(vector<int>& nums, int target) {
        vector<vector<int>>ret;
        sort(nums.begin(), nums.end());
        for(int i = 0;i<nums.size();i++){
            if(i&&nums[i-1] == nums[i])
                continue;
            if(nums[i]+3*nums.back() < target)
                continue;
            if(4*nums[i]>target)
                break;
            int to_find = target - nums[i];
            threeSum(ret, nums, i+1, nums[i], to_find);
        }
        return ret;
    }   
    void threeSum(vector<vector<int>>&ret, vector<int>& nums,int start, int og, int to_find) {
        for(int i = start;i<nums.size();i++){
            if(i!=start&&nums[i-1] == nums[i])
                continue;
            if(nums[i]+2*nums.back() < to_find)
                continue;
            if(3*nums[i]>to_find)
                break;
            
            int target = to_find-nums[i];
            int j = i+1, k = nums.size()-1;
            while(j<k){
                int sum = nums[j]+nums[k];
                if(sum > target)
                    k--;
                else if(sum<target)
                    j++;
                else{
                    ret.push_back({og, nums[i], nums[j], nums[k]});
                    while(j<k && nums[j] == nums[j+1])j++;
                    while(j<k && nums[k] == nums[k-1])k--;
                    j++;
                    k--;
                }
            }
        }
    }
};
```
# use another loop to find three sum