```cpp
class Solution {
public:
    int threeSumClosest(vector<int>& nums, int target) {
        sort(nums.begin(),nums.end());
        int res,tar,l,r;
        int temp=INT_MAX,temp1;
        for(int i=0;i<nums.size()-2;i++){
            tar=target-nums[i];
            if(i>0)
                if(nums[i]==nums[i-1])
                    continue;
            l=i+1;
            r=nums.size()-1;
            while(l<r){
                temp1=(tar-nums[l]-nums[r]);
                // cout<<temp1<<" "<<target<<" "<<tar<<" "<<nums[i]<<" "<<nums[l]<<" "<<nums[r]<<endl;
                if(temp1==0){
                    return target;
                }
                temp=umin(temp,temp1);
                if(temp1<0){
                    while(nums[r--]==nums[r]){
                    if(l>=r)
                            break;
                    }
                }
                else{
                    while(nums[l++]==nums[l]){
                    if(l>=r)
                        break;
                    }
                }
                        
                
                    
            }
        }
        return target-temp;
    }
    int umin(int &a,int &b){
        if(a<0 && b<0){
            return a>b?a:b;
        }else if(a<0){
            return -a<b?a:b;
        }else if(b<0){
            return a<-b?a:b;
        }else
            return a<b?a:b;
    }
};
```
# same with 3sum