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
    vector<TreeNode*> generateTrees(int n) {
        vector<TreeNode*> res;
        if(n==0)
            return res;
        res=generate(1,n);
        return res;
    }
    vector<TreeNode*> generate(int start,int end){
        vector<TreeNode*> res;
        if(start>end)
            res.push_back(NULL);
        
        for(int i=start;i<=end;i++){
            vector<TreeNode*> left=generate(start,i-1);
            vector<TreeNode*> right=generate(i+1,end);
            for(TreeNode* a:left){
                for(TreeNode* b:right){
                    TreeNode* root=new TreeNode(i);
                    root->left=a;
                    root->right=b;
                    res.push_back(root);
                }
            }
        }
        return res;
    }
};
```
# 分治法 