```cpp
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int left=0,right=nums.size()-1;
        int mid;
        while(left<=right){
            mid=(left+right)/2;
            if(nums[mid]==target)
                return mid;
            if(nums[mid]<nums[right]){
                if(nums[mid]<target && nums[right]>=target)
                    left=mid+1;
                else
                    right=mid-1;
            }else{
                if(nums[left]<=target && nums[mid]>target)
                    right=mid-1;
                else
                    left=mid+1;
            }
        }
        return -1;
    }
};
```
# ref： https://www.cnblogs.com/grandyang/p/4325648.html
* mid and right to find the order part(left or right)
* if right part is order,  Determine if the target is on the right
* if left part is order,  Determine if the target is on the left