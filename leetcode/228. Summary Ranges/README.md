```cpp
class Solution {
public:
    vector<string> summaryRanges(vector<int>& nums) {
        vector<string> re;
        if(nums.size()<=0)
            return {};
        if(nums.size()==1)
            return {to_string(nums[0])};
        int start=nums[0];
        string temp;
        for(int i=1;i<nums.size();i++){
            if((long long)nums[i]-nums[i-1]!=1){
                if(nums[i-1]!=start)
                    temp=to_string(start)+"->"+to_string(nums[i-1]);
                else
                    temp=to_string(start);
                re.push_back(temp);
                start=nums[i];                
            }
        }
        if((long long)nums[nums.size()-1]-nums[nums.size()-2]!=1){
            temp=to_string(start);
        }else{
            temp=to_string(start)+"->"+to_string(nums[nums.size()-1]);
        }
        re.push_back(temp);
        return re;
    }
};
```