```cpp
class Solution {
public:
    void rotate(vector<int>& nums, int k) {
        k=k%nums.size();
        int temp;
        for(int i=0;i<nums.size()/2;i++){
            temp=nums[i];
            nums[i]=nums[nums.size()-i-1];
            nums[nums.size()-i-1]=temp;
        }
        for(int i=0;i<k/2;i++){
            temp=nums[i];
            nums[i]=nums[k-i-1];
            nums[k-i-1]=temp;
        }
        for(int i=0;i<(nums.size()-k)/2;i++){
            temp=nums[i+k];
            nums[i+k]=nums[nums.size()-i-1];
            nums[nums.size()-i-1]=temp;
        }
    }
};
//reverse
```
```cpp
class Solution {
public:
    void rotate(vector<int>& nums, int k) {
        k=k%nums.size();
        vector<int> temp;
        for(int i=0;i<k;i++){
            temp.push_back(nums[nums.size()-1-i]);
        }
        int j=1;
        for(int i=nums.size()-k-1;i>-1;i--){
            nums[nums.size()-j++]=nums[i];
        }
        for(int i=0;i<temp.size();i++){
            nums[i]=temp[temp.size()-1-i];
        }
    }
};
```