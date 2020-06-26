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
    vector<int> rightSideView(TreeNode* root) {
        if(root==NULL)
            return {};
        vector<int> res;
        bfs(0,res,root);
        return res;
    }
    void bfs(int n,vector<int> &res,TreeNode* root){
        if(res.size()<=n){
            res.push_back(root->val);
        }else{
            res[n]=root->val;
        }
        if(root->left!=NULL)
            bfs(n+1,res,root->left);
        if(root->right!=NULL)
            bfs(n+1,res,root->right);
        
        
    }
};
```