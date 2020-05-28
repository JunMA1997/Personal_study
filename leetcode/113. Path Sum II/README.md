```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    vector<vector<int>> pathSum(TreeNode* root, int sum) {
        vector<vector<int>> res;
        vector<int> temp;
        helper(res,root,temp,0,sum);
        return res;
    }
    void helper(vector<vector<int>> &res,TreeNode* root,vector<int> &temp,int now,int sum){
        if(root==NULL)
            return;
        now+=root->val;
        if(now==sum){
            if(root->left==NULL && root->right==NULL){
                temp.push_back(root->val);
                res.push_back(temp);
                temp.pop_back();
                return;
            }
            
        }
        temp.push_back(root->val);
        helper(res,root->left,temp,now,sum);
        helper(res,root->right,temp,now,sum);
        temp.pop_back();
    }
};
```