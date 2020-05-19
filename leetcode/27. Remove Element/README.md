```cpp
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        int j=0;
        while( nums.size()-j>1){
            if(nums[nums.size()-1-j]!=val)
                break;
            j++;
        }
        
        for(int i=0;i<nums.size()-j;i++){
            if(nums[i]==val){
                
                nums[i]=nums[nums.size()-1-j]+nums[i];
                nums[nums.size()-1-j]=nums[i]-nums[nums.size()-1-j];
                nums[i]=nums[i]-nums[nums.size()-1-j];;
                j++;
                i--;
            }
        }
        
        return nums.size()-j;
    }
};
```