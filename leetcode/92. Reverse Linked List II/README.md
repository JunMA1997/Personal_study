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
    ListNode* reverseBetween(ListNode* head, int m, int n) {
        if(n==m)
            return head;
        ListNode* p=NULL,*headend,*reverseend,*next,*r,*rev;
        
        if(m==1){
            p=head;
            reverseend=p;
            rev=p;
        }else{
            p=head;
            for(int i=0;i<m-2;i++)   
                p=p->next;
            headend=p;
            p=p->next;
            
            reverseend=p;
            rev=p;
            
        }
        
        next=p->next;
        
        for(int i=0;i<n-m;i++){  
            p=next;
            next=p->next;
            p->next=rev;
            rev=p;
            
        }
        
        reverseend->next=NULL;
        
        if(m==1){
            head=rev;
        }else{
            headend->next=rev;
        }
        reverseend->next=next;
        return head;
    }
};
```
# find the reverse start position, reverse listnode then concat.
* headend is the last of 1st listnode
* rev is reverse(2nd) begin point
* revseend is reverse(2nd) end point
* next is 3rd list point