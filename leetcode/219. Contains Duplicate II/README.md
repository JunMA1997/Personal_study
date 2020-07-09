```cpp
class Solution {
public:
    bool containsNearbyDuplicate(vector<int>& nums, int k) {
        unordered_map<int,int> h;
        for(int i=0;i<nums.size();i++){
            if(i>k){
                h[nums[i-k-1]]--;
            }
            if(h[nums[i]]){
                return true;
            }
                
            h[(nums[i])]++;
        }
        return false;
    }
};
```