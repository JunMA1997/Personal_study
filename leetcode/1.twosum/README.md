# CPP solution:
* ideas:
* * sort(O(nlogn)) the nums and then use two point to find the number(O(n)).finally use origin set to find the index(O(n)).
* CODE:
```CPP
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        vector<int> res;
        vector<int> origin=nums;
        sort(nums.begin(),nums.end());
        int left=0,right=nums.size()-1;
        while(left<right){
            if(nums[left]+nums[right]<target){
                left++;
            }
            if(nums[left]+nums[right]==target){
                break;
            }
            if(nums[left]+nums[right]>target){
                right--;
            }
        }
        for(int i = 0;i < nums.size();i++){
            if(left!=-1)
                if(origin[i]==nums[left]){
                    res.push_back(i);
                    left=-1;
                    continue;
                }
            if(right!=-1)
                if(origin[i]==nums[right]){
                    res.push_back(i);
                    right=-1;
                }
        } 
        return res;
    }
};
```