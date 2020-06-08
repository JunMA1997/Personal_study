```cpp
class Solution {
public:
    vector<int> postorderTraversal(TreeNode* root) {
        if(root==NULL)
            return {};
        vector<int> res;
        vector<TreeNode*> s;
        s.push_back(root);
        TreeNode* head=root;
        while(s.size()){
            TreeNode* temp=s.back();
            if((!temp->left && !temp->right)||temp->left==head||temp->right==head){
                s.pop_back();
                res.push_back(temp->val);
                head=temp;
            }else{
                if(temp->right)
                    s.push_back(temp->right);
                if(temp->left)
                    s.push_back(temp->left);
            }
        }
        return res;
    }
};
```
# a question:
* what is the difference between stack and vector?