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
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        ListNode* p=head;
      
        int len=0;
        while(p!=NULL){
            len++;
            p=p->next;
        }
        if(len==1)
            return NULL;
        n=len-n;
        if(n==0)
            return head->next;
        p=head;
        
        for(int i=0;i<n-1;i++){
            p=p->next;
        }
        p->next=p->next->next;
        
        return head;
    }
};
```