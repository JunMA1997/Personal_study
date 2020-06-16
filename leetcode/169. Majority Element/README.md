```cpp
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        int n=nums.size();
        unordered_map<int,int>m;
        for(int i=0;i<n;i++){
            m[nums[i]]++;
        }
        for(int i=0;i<nums.size();i++){
            if(m.find(nums[i])->second>nums.size()/2)
                return nums[i];
        }
        return 0;
    }
};
```