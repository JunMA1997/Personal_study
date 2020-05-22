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
    vector<int> inorderTraversal(TreeNode* root) {
        vector<int> res;
        if(root==NULL){
            return res;
        }
        vector<TreeNode*> temp;
        TreeNode* p=root;
        while(p || temp.size()!=0){
            while(p){
                temp.push_back(p);
                p=p->left;
            }
            p=temp[temp.size()-1];
            temp.pop_back();
            res.push_back(p->val);
            p=p->right;
        }
        return res;
    }
};
```
# inorder（前序遍历） iteratively