```cpp
class Solution {
public:
    int findMin(vector<int>& nums) {

        int left=0,right=nums.size()-1;
        int mid;
        while(left<right){
            mid=(left+right)/2;
            // cout<<left<<" "<<mid<<" "<<right<<" "<<nums[mid]<<endl;
            if(nums[mid]<=nums[right] && nums[mid]>=nums[left])
                return nums[left];
            else{
                if(nums[mid]<=nums[right])
                    right=mid;
                else
                    left=mid+1;
            }
        }
        // cout<<left<<" "<<mid<<" "<<right<<endl;
        return nums[right];
    }
};
```