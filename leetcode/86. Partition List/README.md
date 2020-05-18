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
    ListNode* partition(ListNode* head, int x) {
        ListNode *res=NULL,*less=NULL,*bigbegin=NULL,*lessbegin=NULL,*big=NULL,*p,*q=head;
        while(q!=NULL){
            p=q;
            q=q->next;
            
            // cout<<p->val<<" ";
            if(p->val<x){
                if(lessbegin==NULL){
                    lessbegin=p;
                    less=p;
                    p->next=NULL;
                }else{
                    less->next=p;
                    less=p;
                    p->next=NULL;
                }
            }else{
                if(bigbegin==NULL){
                    bigbegin=p;
                    big=p;
                    p->next=NULL;
                }else{
                    big->next=p;
                    big=p;
                    p->next=NULL;
                }
            }            
              
            
        }
        if(less!=NULL){
            less->next=bigbegin;      
        }else{
            lessbegin=bigbegin;
        }
        
        res=lessbegin;    
        
        return res;
    }
};
```