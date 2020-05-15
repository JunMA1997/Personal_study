```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        for(int i=2;i<nums.size();){
            if(nums[i]==nums[i-2])
                nums.erase(nums.begin()+i);
            else
                i++;
        }
        return nums.size();
    }
};
```
# judge i-2 equals to i? delete:continue