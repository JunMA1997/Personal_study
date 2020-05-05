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
    ListNode* rotateRight(ListNode* head, int k) {
        if(head==NULL)
            return head;
        ListNode *p=head,*r=head;
        int size=0;
        while(p!=NULL){
            // cout<<size;
            size++;
            p=p->next;
        }
        if(k%size==0)
            return head;
        p=head;
        
        for(int i=0;i<size-k%size;i++){
            if(p->next==NULL){
                r=p;
                p=head;
            }else{
                r=p;
                p=p->next;
            }   
        }
        r->next=NULL;
        r=p;
        while(r->next!=NULL){
            r=r->next;
        }
        r->next=head;
        return p;
    }
};
```
# easy solution with high memory use