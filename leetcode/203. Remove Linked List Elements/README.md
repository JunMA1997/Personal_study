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
class Solution {
public:
    ListNode* removeElements(ListNode* head, int val) {
        ListNode *res=new ListNode(),*last=res,*p=head,*next=head;
        res->next=head;
        while(p!=NULL){
            next=p->next;
            if(p->val==val){
                last->next=next;       
                // free(p);
            }else{
                last=p;
            }
            p=next;
        }
        return res->next;
    }
};
```