```cpp
class Solution {
public:
    void nextPermutation(vector<int>& nums) {
        if(nums.size()==0)
            return;
        int m=-1,i;
        for(i=nums.size()-2;i>-1;i--){
            if(nums[i+1]>nums[i]){
                m=i;
                break;
            }
        }
        if(m!=-1){
            for(i=m+1;i<nums.size();i++){
                if(nums[i]<=nums[m])
                    break;
            }
            swap(nums[i-1],nums[m]);          
        }
        m++;
        int n=(nums.size()-m)/2;
        for(i=0;i<n;i++){
            swap(nums[i+m],nums[nums.size()-1-i]);
        }
    }
};
```