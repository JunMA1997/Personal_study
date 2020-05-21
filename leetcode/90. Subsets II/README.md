```cpp
class Solution {
public:
    vector<vector<int>> subsetsWithDup(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        vector<vector<int>> res;
        vector<int> temp;
        test(res,temp,nums,0);
        sort(res.begin(),res.end());
        res.erase(unique(res.begin(),res.end()),res.end());
        return res;
    }
    void test(vector<vector<int>> &res,vector<int>& temp,vector<int>& nums,int k){
        
        res.push_back(temp);
        
        for(int i=k;i<nums.size();i++){
            
            temp.push_back(nums[i]);
            test(res,temp,nums,i+1);
            temp.pop_back();
        }
    }
};
```
# easy solution with subset

```cpp
class Solution {
public:
    vector<vector<int>> subsetsWithDup(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        vector<vector<int>> res;
        vector<int> temp;
        test(res,temp,nums,0);
        return res;
    }
    void test(vector<vector<int>> &res,vector<int>& temp,vector<int>& nums,int k){
        
        res.push_back(temp);
        
        for(int i=k;i<nums.size();i++){
            
            temp.push_back(nums[i]);
            test(res,temp,nums,i+1);
            temp.pop_back();
            while (i+1 < nums.size()) {
                if(nums[i] != nums[i + 1] )
                    break;
                i++;
            }
                
        }
    }
};
```
# skip repeat node.