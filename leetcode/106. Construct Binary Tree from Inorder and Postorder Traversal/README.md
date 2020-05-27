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
    TreeNode* buildTree(vector<int>& inorder, vector<int>& postorder) {
        return helper(inorder,postorder,0,inorder.size()-1,0,postorder.size()-1);
    }
    TreeNode* helper(vector<int>& inorder, vector<int>& postorder,int ileft,int iright,int pleft,int pright){
        if(pleft>pright || ileft>iright)
            return NULL;
        int i;
        for(i=ileft;i<iright;i++){
            if(postorder[pright]==inorder[i])
                break;
        }
        // cout<<i;
        TreeNode* root=new TreeNode(postorder[pright]);
        root->left=helper(inorder,postorder,ileft,i-1,pleft,pleft+i-ileft-1);
        root->right=helper(inorder,postorder,i+1,iright,pleft+i-ileft,pright-1);
        return root;
    }
};
```