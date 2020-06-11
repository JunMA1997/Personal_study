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
    ListNode* sortList(ListNode* head) {
        if(!head || !head->next)
            return head;
        ListNode *slow = head, *fast = head, *pre = head;
        while (fast && fast->next) {
            pre = slow;
            slow = slow->next;
            fast = fast->next->next;
        }
        pre->next=NULL;
        return merge(sortList(head),sortList(slow));
    }
    ListNode* merge(ListNode* left,ListNode* right){
        ListNode* start=new ListNode();
        ListNode* cur=start;
        while(left && right){
            if(left->val<right->val){
                cur->next=left;
                left=left->next;
            }else{
                cur->next=right;
                right=right->next;
            }
            cur=cur->next;
        }
        if(left)
            cur->next=left;
        if(right)
            cur->next=right;
        return start->next;
    }
};
```
# 归并排序的应用，可以用快排但是始终没有搞明白为啥快排会更慢