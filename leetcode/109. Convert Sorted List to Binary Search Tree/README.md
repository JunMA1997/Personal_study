```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
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
    TreeNode* sortedListToBST(ListNode* head) {
        if(!head)
            return NULL;
        if(!head->next)
            return new TreeNode(head->val);
        ListNode *slow=head,*fast=head,*last=head;
        while(fast->next &&fast->next->next){
            last=slow;
            fast=fast->next->next;
            slow=slow->next;
        }
        fast=slow->next;
        last->next=NULL;
        TreeNode *root=new TreeNode(slow->val);
        if(head!=slow)
            root->left=sortedListToBST(head);
        root->right=sortedListToBST(fast);
        return root;
    }

};
```