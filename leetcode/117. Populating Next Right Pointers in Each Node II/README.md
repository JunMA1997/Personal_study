```cpp
/*
// Definition for a Node.
class Node {
public:
    int val;
    Node* left;
    Node* right;
    Node* next;

    Node() : val(0), left(NULL), right(NULL), next(NULL) {}

    Node(int _val) : val(_val), left(NULL), right(NULL), next(NULL) {}

    Node(int _val, Node* _left, Node* _right, Node* _next)
        : val(_val), left(_left), right(_right), next(_next) {}
};
*/

class Solution {
public:
    Node* connect(Node* root) {
        queue<Node*> q;
        Node* t;
        if(!root)
            return root;
        q.push(root);
        while(q.size()){
            for(int i=q.size();i>0;i--){
                t=q.front();
                q.pop();
                if(t->left)
                    q.push(t->left);
                if(t->right)
                    q.push(t->right);
                if(i==1){
                    t->next==NULL;
                    break;
                }
                t->next=q.front();
            }
        }
        return root;
    }
};
```
# in 116, consider this question.

```cpp
/*
// Definition for a Node.
class Node {
public:
    int val;
    Node* left;
    Node* right;
    Node* next;

    Node() : val(0), left(NULL), right(NULL), next(NULL) {}

    Node(int _val) : val(_val), left(NULL), right(NULL), next(NULL) {}

    Node(int _val, Node* _left, Node* _right, Node* _next)
        : val(_val), left(_left), right(_right), next(_next) {}
};
*/

class Solution {
public:
    Node* connect(Node* root) {
        
        Node* t=root;
        if(!root)
            return root;
        while(t){
            Node* pre=t;
            Node* now=NULL;
            while(pre){
                if(pre->left){
                    if(now==NULL){
                        now=pre->left;
                    }else{
                        now->next=pre->left;
                        now=now->next;
                    }
                }
                if(pre->right){
                    if(now==NULL){
                        now=pre->right;
                    }else{
                        now->next=pre->right;
                        now=now->next;
                    }
                }
                pre=pre->next;
            }
            while(t){
                if(t->left){
                    t=t->left;
                    break;
                }
                if(t->right){
                    t=t->right;
                    break;
                }
                t=t->next;    
            }
            
        }
        return root;
    }
};
```