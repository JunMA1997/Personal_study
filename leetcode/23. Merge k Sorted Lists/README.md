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
    ListNode* mergeKLists(vector<ListNode*>& lists) {
        if(lists.size()<=0)
            return NULL;
        ListNode* p;
        for(int i=0;i<lists.size();i+=2){
            // cout<<lists.size()<<" "<<i<<endl;
            if(i==lists.size()-1)
                return lists[i];
            // cout<<i;

            // lists.pop_back();
            // lists.pop_back();
            else
                lists.push_back(mergeTwoLists(lists[i],lists[i+1]));
        }
        
        return lists[lists.size()-1];
    }
};
```
# using merge two