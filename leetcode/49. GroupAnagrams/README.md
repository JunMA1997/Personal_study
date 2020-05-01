```cpp
class Solution {
public:    
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        vector<int> table{2,3,5,7,11,13,17,19,23,29,31,37,41,43,47,53,59,61,67,71,73,79,83,89,97,101};
        vector<unsigned int> temp2;
        vector<vector<string>> res;
        // return res;
        long long hash;
        int pos;
        for(int i=0;i<strs.size();i++){
            hash=1;
            for(int j=0;j<strs[i].size();j++){
                hash*=table[strs[i][j]-'a'];
                hash=hash%UINT_MAX;
            }           
            pos=check(temp2,hash);
            if(pos==temp2.size()){
                temp2.push_back(hash);                
                res.push_back(vector<string> {strs[i]});
            }
            else{
                res[pos].push_back(strs[i]);
            }
        }
        return res;
    }
    int check(vector<unsigned int> &t,int n){
        for(int j=0;j<t.size();j++){
            if(t[j]==n)
                return j;
        }
        return t.size();
    }
};
```
# my solution:
* i think problem is in check function, it takes too much time.
```cpp
class Solution {
public:    
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        vector<int> table{2,3,5,7,11,13,17,19,23,29,31,37,41,43,47,53,59,61,67,71,73,79,83,89,97,101};
        vector<vector<string>> res;
        map<unsigned int,vector<string>> result;
        long long hash;
        unsigned int pos;
        for(int i=0;i<strs.size();i++){
            hash=1;
            for(int j=0;j<strs[i].size();j++){
                hash*=table[strs[i][j]-'a'];
                hash=hash%UINT_MAX;
            }    
            pos=hash;
            result[pos].push_back(strs[i]);
        }
        
        for( map<unsigned int,vector<string>>::iterator it = result.begin(); it != result.end(); ++it ) {
            res.push_back( it->second );
        }
        return res;
    }
};
```
# using map to decrease time comp,it worked.




