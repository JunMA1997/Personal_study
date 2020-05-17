```cpp
class Solution {
public:
    bool search(vector<int>& nums, int target) {
        if(nums.size()<1){
            return false;
        }
        int left=0,right=nums.size()-1;
        while(nums[left]==nums[right] && right>=1){
            right--;
        }
        if(right!=nums.size()-1)
            right++;
        if(right==0)
            return target==nums[0];
        
        int mid,r=-1;
        while(left<right){
            mid=(left+right)/2;
            if(nums[mid]>nums[mid+1])
            {
                r=mid;
                break;
            }
            
            if(nums[mid]>=nums[left])
            {
                left=mid+1;
                continue;
            }
            else 
                right=mid;    
        }
        if(target<nums[0]){
            left=++r;
            right=nums.size();
        }
        else{
            left=0;
            right=nums.size();
            if(r>=0)
                right=++r;            
        }  
        //cout<<left<<right<<endl;
        while (left < right){
            mid = (right + left) / 2;
            if (nums[mid] == target) 
                return true;
            else 
                if (nums[mid] < target) 
                    left = mid + 1;
            else 
                right = mid;
        }        
        return false;
    }
};
```