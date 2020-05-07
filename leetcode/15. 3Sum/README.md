# same like 2 sum
* use 1 loop to get the first then 2 sum=target
```cpp
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        vector<vector<int>> res;
        if(nums.size()<3)
            return res;
        
        vector<int> temp(3);
        int l,r,i,target=-1;
        
        for(i=0;i<nums.size()-2;i++){
            if(nums[i]>0 || nums[i]==-target)
                continue;
            target=-nums[i];            
            r=nums.size()-1;
            l=i+1;
            while(l<r){
                // cout<<target<<nums[l]<<" "<<nums[r]<<endl;
                  
                if(nums[l]+nums[r]<target){
                    while(nums[l++]==nums[l])
                        if(l>=r)
                            break;
                    continue;
                }                   
                  
                if(nums[l]+nums[r]>target){
                    while(nums[r--]==nums[r])
                        if(l>=r)
                            break;
                    continue;
                }
                if(nums[l]+nums[r]==target){
                    temp[0]=nums[i];
                    temp[1]=nums[l];
                    temp[2]=nums[r];
                    while(nums[r--]==nums[r])
                        if(l>=r)
                            break;
                    while(nums[l++]==nums[l])
                        if(l>=r)
                            break;
                    res.push_back(temp);
                    continue;
                }                 
                    
                    
            }
        }
        return res;
    }
};
```