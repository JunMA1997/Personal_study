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
    bool isValidBST(TreeNode* root) {
        return isValid(root,long(INT_MIN)-1,long(INT_MAX)+1,false);
    }
    bool isValid(TreeNode* root,long lowest,long upper,bool init){
        // cout<<lowest<<" "<<upper<<endl;
        if(root==NULL)
            return true;
        if(init && (lowest>=root->val || upper<=root->val))
            return false;
        
        if(!isValid(root->left,lowest,root->val,true))
            return false;
        if(!isValid(root->right,root->val,upper,true))
            return false;
        return true;
    }
};
```
# lower and upper to judge;