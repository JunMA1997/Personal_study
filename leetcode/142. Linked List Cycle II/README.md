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
    ListNode *detectCycle(ListNode *head) {
        ListNode *fast=head,*slow=head;
        while(fast!=NULL && fast->next!=NULL){
            fast=fast->next->next;
            slow=slow->next;
            if(slow==fast)
                break;
        }
        if(!fast || !fast->next)
            return NULL;
        slow=head;
        while(fast!=slow){
            fast=fast->next;
            slow=slow->next;
        }
        return fast;
    }
};
```
# two point, slow and fast, same as linked list cycle. extr loop after find the same point:slow=head
```cpp
class Solution {
public:
    ListNode *detectCycle(ListNode *head) {
        unordered_set<ListNode*> check; 
        while(head!=NULL){
            if(check.count(head))
                return head;
            check.insert(head);
            head=head->next;
        }
        return NULL;
    }
};
```
# easy understand solution