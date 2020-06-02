# O($\log(n)$)
```cpp
class Solution {
public:
    vector<int> searchRange(vector<int>& nums, int target) {
        int left=0,right=nums.size(),mid;
        int rl;
        while(left<right){
            mid=(left+right)/2;
            if(nums[mid]<target)
                left=mid+1;
            else
                right=mid;
        }
        if(right==nums.size() || nums[right]!=target) 
            return {-1,-1};
        rl=right;
        right=nums.size();
        while(left<right){
            mid=(left+right)/2;
            if(nums[mid]==target)
                left=mid+1;
            else
                right=mid;
        }
        return {rl,right-1};
    }
};
```
# O(n) in worest.
```cpp
class Solution {
public:
    vector<int> searchRange(vector<int>& nums, int target) {
        vector<int> re;
        int left=0;
        int right=nums.size();
        int l,r,m;
        int mid;
        
        while(left<right){
            
            mid=(left+right)/2;
            cout<<nums[mid];
            if(nums[mid]==target)
            {
                left=mid;
                right=mid;
                while(1){
                    if(--left<0)
                        break;
                    if(nums[left]!=target)
                    {
                        re.push_back(++left);
                        break;
                    }
                    
                }
                if(re.size()==0)
                    re.push_back(0);
                while(1){
                    if(++right>=nums.size())
                        break;
                    if(nums[right]!=target)
                    {
                        re.push_back(--right);
                        break;
                    }
                    
                }
                if(re.size()==1)
                {
                    re.push_back(nums.size()-1);
                }
                    
                    
                return re;
                
            }
            else if(nums[mid]<target){
                left=mid+1;
                continue;
            }
            else
            {
                right=mid;
                continue;
            }
        }
        
        re.push_back(-1);
        re.push_back(-1);
        return re;
    }
};
```