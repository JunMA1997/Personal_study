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
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        ListNode *PA=headA,*PB=headB;
        bool AR=true,BR=true;
        while(PA && PB){
            if(PA==PB)
                return PA;
            if(PA->next==NULL && AR){
                PA=headB;
                AR=false;
            }                
            else
                PA=PA->next;
            if(PB->next==NULL && BR){
                BR=false;
                PB=headA;
            }                
            else
                PB=PB->next;
        }
        return NULL;
    }

};
```
# two point