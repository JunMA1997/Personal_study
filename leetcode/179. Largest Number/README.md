```cpp
class Solution {
public:
    string largestNumber(vector<int>& nums) {
        sort(nums.begin(),nums.end(),sortFunction);
        if(!nums.size())
            return "";
        if(!nums[0])
            return "0";
        string res;
        for(int i=0;i<nums.size();i++)
            res+=to_string(nums[i]);
        return res;
    }
private:
    static bool sortFunction(int i,int j){
        string a=to_string(i),b=to_string(j);
        return a+b>b+a;
    }
};
```