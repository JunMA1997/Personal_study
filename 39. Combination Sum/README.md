# Description:
* Given a set of candidate numbers (candidates) (without duplicates) and a target number (target), find all unique combinations in candidates where the candidate numbers sums to target. The same repeated number may be chosen from candidates unlimited number of times.
* * Note:
* * * All numbers (including target) will be positive integers.
* * * The solution set must not contain duplicate combinations.

# solution1:
* DFS:
class Solution {
public:
    vector<vector<int>> combinationSum(vector<int>& candidates, int target) {
        vector<vector<int>> res;
        vector<int> temp;
        combinationSumDFS(candidates,0,target,temp,res);
        return res;
    }
    void combinationSumDFS(vector<int>& candidates,int start,int target,vector<int> temp,vector<vector<int>> &res){
        if(target<0)
            return;
        if(target==0){
            res.push_back(temp);
            return;
        }
            
        for(int i = start;i < candidates.size();i++){
            temp.push_back(candidates[i]);
            combinationSumDFS(candidates,i,target-candidates[i],temp,res);
            temp.pop_back();
        }
    }
};

* This solution is really slow, but can improve by sort.

class Solution {
public:
    vector<vector<int>> combinationSum(vector<int>& candidates, int target) {
        vector<vector<int>> res;
        vector<int> temp;
        sort(candidates.begin(), candidates.end()); 
        combinationSumDFS(candidates,0,target,temp,res);
        return res;
    }
    void combinationSumDFS(vector<int>& candidates,int start,int target,vector<int> temp,vector<vector<int>> &res){
        if(target<0)
            return;
        if(target==0){
            res.push_back(temp);
            return;
        }
            
        for(int i = start;i < candidates.size();i++){
            if(target-candidates[i]<0)
                break;
            temp.push_back(candidates[i]);
            combinationSumDFS(candidates,i,target-candidates[i],temp,res);
            temp.pop_back();
        }
    }
};
* This one is much better than first one, but still not good.