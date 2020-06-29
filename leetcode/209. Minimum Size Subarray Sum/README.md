```cpp
class Solution {
public:
    int minSubArrayLen(int s, vector<int>& nums) {
        int i=0,j=0,sum=0,ans=0;
        for(;j<nums.size();j++){
            sum+=nums[j];
            while(sum>=s){
                if(!ans){
                    ans=j-i+1;
                }else{
                    ans=min(j-i+1,ans);                    
                }
                sum-=nums[i++];
            }
        }
        return ans;
    }
};
```