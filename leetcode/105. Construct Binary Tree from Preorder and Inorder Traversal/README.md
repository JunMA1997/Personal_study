```cpp
class Solution {
public:
    TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) {
        return helper(preorder,inorder,0,preorder.size()-1,0,inorder.size()-1);        
    }
    TreeNode* helper(vector<int>& preorder, vector<int>& inorder, int pleft,int pright,int ileft,int iright){
        
        if(pleft>pright || ileft>iright)
            return NULL;
        int i;
        for(i=ileft;i<iright;i++){
            if(preorder[pleft]==inorder[i])
                break;
        }
        TreeNode *root=new TreeNode(preorder[pleft]);
        root->left=helper(preorder,inorder,pleft + 1,pleft + i - ileft,ileft,i-1);
        root->right=helper(preorder,inorder,pleft + i - ileft+1,pright,i+1,iright);
        return root;
    }
};
```