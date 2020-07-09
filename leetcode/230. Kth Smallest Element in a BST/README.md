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
    int kthSmallest(TreeNode* root, int k) {
        // return 0;
        stack<TreeNode*> s;
        TreeNode* p=root;
        while(p){

            s.push(p);
            p=p->left;
        }
        for(int i=0;i<k-1;i++){
            TreeNode* p=s.top();
            s.pop();
            p=p->right;
            while(p){
                s.push(p);
                p=p->left;
            }
            
        }
        return s.top()->val;
    }
};
```