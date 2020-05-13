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
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        ListNode* head=NULL,*p=NULL;
        while(l1!=NULL || l2!=NULL){
            // cout<<l1->val<<l2->val<<endl;
            if(l1==NULL){
                if(head==NULL){
                    head=l2;
                    return head;
                }else{
                    p->next=l2;
                    return head;
                }
            }
            else if(l2==NULL){
                if(head==NULL){
                    head=l1;
                    return head;
                }else{
                    p->next=l1;
                    return head;
                }
            }else{
                if(head==NULL){
                    if(l1->val>l2->val){
                        head=l2;
                        p=l2;
                        l2=l2->next;
                    }else{
                        head=l1;
                        p=l1;
                        l1=l1->next;
                    }
                }else{
                    if(l1->val>l2->val){
                        p->next=l2;
                        p=p->next;
                        l2=l2->next;
                    }else{
                        p->next=l1;
                        p=p->next;
                        l1=l1->next;
                    }
                }
            }
        }
        return head;
    }
};
```
# easy solution, point exercise