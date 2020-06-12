```cpp
class Solution {
public:
    int maxProduct(vector<int>& nums) {
        vector<int> dpmax(nums.size(),INT_MIN),dpmin(nums.size(),INT_MAX);
        dpmax[0]=nums[0];
        dpmin[0]=nums[0];
        int res=nums[0];
        for(int i=1;i<nums.size();i++){
            dpmax[i]=max(max(dpmin[i-1]*nums[i],dpmax[i-1]*nums[i]),nums[i]);
            dpmin[i]=min(min(dpmin[i-1]*nums[i],dpmax[i-1]*nums[i]),nums[i]);
            res=max(dpmax[i],res);
        }
        return res;
    }
};
```
# two dp, one record min and the other record max