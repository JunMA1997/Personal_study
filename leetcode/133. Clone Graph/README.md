```cpp
/*
// Definition for a Node.
class Node {
public:
    int val;
    vector<Node*> neighbors;
    
    Node() {
        val = 0;
        neighbors = vector<Node*>();
    }
    
    Node(int _val) {
        val = _val;
        neighbors = vector<Node*>();
    }
    
    Node(int _val, vector<Node*> _neighbors) {
        val = _val;
        neighbors = _neighbors;
    }
};
*/

class Solution {
public:
    Node* cloneGraph(Node* node) {
        unordered_map<int,Node*> check;
        return helper(check,node);
    }
    Node* helper(unordered_map<int,Node*> &check,Node* node){
        if(node==NULL)
            return NULL;
        if(check.count(node->val)!=0){
             return check.find(node->val)->second;
        }
        Node *res=new Node(node->val);
        check.insert(pair<int,Node*>(node->val,res));
        for(int i=0;i<node->neighbors.size();i++){
            res->neighbors.push_back(helper(check,node->neighbors[i]));
        }
        return res;
    }
};
```