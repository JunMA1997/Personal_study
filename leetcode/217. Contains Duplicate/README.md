```cpp
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        unordered_map<int,int> ma;
        for(int i = 0; i < nums.size(); i++){
           if(ma[nums[i]] != 0)
               return true;
            ma[nums[i]]++;
        }
        return false;
    }
};
```