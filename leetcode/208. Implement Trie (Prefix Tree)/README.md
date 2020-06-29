```cpp
class Trie {
private:
    typedef struct Tree{
        bool have;
        Tree *leaf[26];
        Tree(){
            have=false;
            memset(leaf,0,sizeof(leaf));
        }
    }Tree;
    Tree *root;
public:
    /** Initialize your data structure here. */
    
    Trie() {
        root=new Tree();
        root->have=true;
    }
    
    /** Inserts a word into the trie. */
    void insert(string word) {
        Tree *p=root;
        for(int i=0;i<word.size();i++){
           if(p->leaf[word[i]-'a']!=NULL)
               p=p->leaf[word[i]-'a'];
           else{
               Tree *n=new Tree();
               p->leaf[word[i]-'a']=n;
               p=n;
           }
        }
        p->have=true;
    }
    
    /** Returns if the word is in the trie. */
    bool search(string word) {
        Tree *p=root;
        for(int i=0;i<word.size();i++){
            if(p->leaf[word[i]-'a']==NULL)
                return false;
            else
                p=p->leaf[word[i]-'a'];
        }
        return p->have;
    }
    
    /** Returns if there is any word in the trie that starts with the given prefix. */
    bool startsWith(string prefix) {
        Tree *p=root;
        for(int i=0;i<prefix.size();i++){
            if(p->leaf[prefix[i]-'a']==NULL)
                return false;
            else
                p=p->leaf[prefix[i]-'a'];
        }
        return true;
    }
};

/**
 * Your Trie object will be instantiated and called as such:
 * Trie* obj = new Trie();
 * obj->insert(word);
 * bool param_2 = obj->search(word);
 * bool param_3 = obj->startsWith(prefix);
 */
```
