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
    ListNode* deleteDuplicates(ListNode* head) {
        ListNode *res=NULL,*last=NULL,*p;
        bool flag;
        while(head!=NULL){ 
            // cout<<"1";
            p=head->next;
            flag=false;
            while(p!=NULL){
                if(head->val!=p->val)
                    break;
                p=p->next;
                flag=true;
            }
            if(flag){
                head=p;
                continue;
            }
            if(res==NULL){
                res=head;
                last=head;
            }else{
                last->next=head;
                last=head;
                
            }
            head=head->next;
        }
        if(last!=NULL)
            last->next=NULL;
        return res;
    }
};
```