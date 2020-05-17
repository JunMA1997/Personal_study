```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* reverseKGroup(ListNode* head, int k) {
        
        ListNode* begin;
        ListNode* end;
        ListNode* p;
        ListNode* b;
        ListNode* lb=nullptr;
        begin=head;
        int n=0;
        end=head;
        while(end!=nullptr){
            n++;
            
            if(n==k)
                head=end;
            end=end->next;
        }
        if(n/k==0)
            return head;
        end=begin;
        p=begin;
        
        for(int i=0;i<n/k;i++){
            
            b=p;
            end=p;
            p=p->next;
            end->next=begin;
            for(int j=0;j<k-1;j++){
                //cout<<b->val<<"<-"<<end->val<<" "<<p->val<<endl;
                
                end=p;   
                
                p=p->next;
                end->next=b;  
                
                b=end;
                
            }
            
            begin->next=p;
            
            if(lb!=nullptr)
                lb->next=end;
            lb=begin;
            begin=p;
            
           
            
        }
        return head;
        
    }
};
```