# a good solution()
* compare to my solution, this solution use one loop and in line if to have less coding part and process time. 98.82%
```CPP
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
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode* ans=NULL;
        ListNode *prev=NULL;
        bool carry=0;
        int sum;
        while(l1!=NULL || l2!=NULL){
            sum=carry+(l1?l1->val:0)+(l2?l2->val:0);
            carry=(sum>=10)?1:0;
            sum=sum%10;
            ListNode* temp=new ListNode(sum);
            if(not ans){
                ans=temp;
                prev=ans;
            }else{
                prev->next=temp;
                prev=prev->next;
            }
            
            if(l1){
                l1=l1->next;
            } 
            if(l2){
                l2=l2->next;
            }
        }
        if(carry){
            prev->next=new ListNode(carry);
        }
        return ans;
    }
};
```

# my solution: 90%
```CPP
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
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        int add=0;
        ListNode *start=NULL;
        ListNode *p,*r;
        
        while(l1 != NULL && l2 != NULL){
            p=new ListNode;
            p->next=NULL;
            int val=l1->val+l2->val+add;
            
            if(val>=10){
                val=val-10;
                add=1;
            }
            else
                add=0;
            p->val=val;            
            if(start==NULL){
                start=p;
                r=p;
            }
            else
            {
                r->next=p;
                r=p;
            }
            l1=l1->next;
            l2=l2->next;       
        }
        while(l1!=NULL){
            int val=l1->val+add;
            if(val>9){
                val-=10;
                add=1;
            }
            else
                add=0;
            p=new ListNode(val);
            p->next=NULL;
            r->next=p;
            r=p;
            l1=l1->next;
        }
        while(l2!=NULL){
            int val=l2->val+add;
            if(val>9){
                val-=10;
                add=1;
            }
            else
                add=0;
            p=new ListNode(val);
            p->next=NULL;
            r->next=p;
            r=p;
            l2=l2->next;
        }
        if(add==1){
            p=new ListNode(1);
            r->next=p;
        }
        return start;
    }
};
```