```cpp
/*
// Definition for a Node.
class Node {
public:
    int val;
    Node* next;
    Node* random;
    
    Node(int _val) {
        val = _val;
        next = NULL;
        random = NULL;
    }
};
*/

class Solution {
public:
    Node* copyRandomList(Node* head) {
        Node *res=NULL,*p,*last;
        unordered_map<Node*,Node*> check;
        while(head!=NULL){
            if(check.count(head)!=0){
                p=check.find(head)->second;
            }else{
                p=new Node(head->val);        
                check.insert(pair<Node*,Node*>(head,p));
            }
            if(res==NULL){
                res=p;
                last=p;
            }else{
                last->next=p;
                last=p;
            }
            if(head->random!=NULL){
                if(check.count(head->random)!=0){
                    p->random=check.find(head->random)->second;
                }else{
                    Node *temp=new Node(head->random->val);
                    check.insert(pair<Node*,Node*>(head->random,temp));
                    p->random=temp;
                        
                }
            }
            head=head->next;
            
        }
        return res;
        
    }
}
```