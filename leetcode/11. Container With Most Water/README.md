```cpp
class Solution {
public:
    int maxArea(vector<int>& height) {
        int l=0,r=height.size()-1;
        int now=0;
        int max=0;
        int temp=0;
        while(l<r){
            
            if(height[l]<height[r]){
                if(height[l]<=now){
                    l++;
                    continue;
                }                    
                temp=height[l]*(r-l);
                if(temp>max){
                    max=temp;
                    now=height[l];
                }
                    
                l++;
            }else{
                if(height[r]<=now){
                    r--;
                    continue;
                }
                    
                temp=height[r]*(r-l);
                
                if(temp>max){
                    max=temp;
                    now=height[r];
                }
                    
                r--;
            }
            
        }
        return max;
    }
};
```
# easy solution