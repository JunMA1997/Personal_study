```cpp
class Solution {
public:
    double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
        if(nums1.size()>nums2.size()){
            return findMedianSortedArrays(nums2,nums1);
        }
        int l=0,r=nums1.size();
        while(l<=r){
            int pos1=(l+r)/2;
            int pos2=(nums1.size()+nums2.size()+1)/2-pos1;
            // cout<<pos1<<pos2;
            int maxLeftX= (pos1==0) ? INT_MIN:nums1[pos1-1];
            int minRightX= (pos1==nums1.size())? INT_MAX:nums1[pos1];
            int maxLeftY= (pos2==0) ? INT_MIN:nums2[pos2-1];
            int minRightY= (pos2==nums2.size())? INT_MAX:nums2[pos2];
            if(minRightX>=maxLeftY && minRightY>=maxLeftX){
                if((nums1.size()+nums2.size())%2==0){
                    return ((max(maxLeftX,maxLeftY)+min(minRightX,minRightY))/2.0);
                }
                else
                    return max(maxLeftX,maxLeftY);
            }
            if(maxLeftX>minRightY)
                r=pos1-1;            
            else
                l=pos1+1;
        }
        return 0.0;
    }
};
```
# binary search
* REF: https://www.youtube.com/watch?v=LPFhl65R7ww&t=1013s
* The shorter length is nums1, call the function again with the right order.
* binary search to find a point that left1 <= right2, left2 <= right1, then return the right value(even and odd judge)
* if left1 >= right2 means we need to left shift(r=mid)
* if right1 <= left2 means we need to right shift(l=mid) 