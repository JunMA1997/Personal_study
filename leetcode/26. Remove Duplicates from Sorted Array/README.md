```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        if(nums.size()<1)
            return 0;
        int j=0;
        for(int i=1;i<nums.size();i++){
            if(nums[i]!=nums[j] )
                nums[++j]=nums[i];           
                
        }
        // cout<<endl;
    
        return j+1;
    }
};
```
# fast solution
```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        vector<int>::iterator k = nums.begin();
        for(int i=1;i<nums.size();){
            if(nums[i]==nums[i-1]){                
                nums.erase(k+i);
            }else
                i++;
        }   
        return nums.size();
    }
};
```
# easy solution but slow.