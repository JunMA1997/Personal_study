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
    ListNode* swapPairs(ListNode* head) {
        ListNode *p=head,*pnext,*pnextnext,*res=NULL,*l;
        while(p!=NULL){
            if(p->next==NULL){
                if(res!=NULL)
                    return res;
                else
                    return head;
            }
            if(res==NULL){
                res=p->next;
            }else{
                l->next=p->next;
            }
            pnext=p->next;
            pnextnext=pnext->next;
            
            pnext->next=p;
            p->next=pnextnext;
            
            l=p;
            p=pnextnext;
        }
        return res;
    }
};
```