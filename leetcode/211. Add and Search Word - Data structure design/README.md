```cpp
class WordDictionary {
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
    WordDictionary() {
        root=new Tree();
    }
    
    /** Adds a word into the data structure. */
    void addWord(string word) {
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
    
    /** Returns if the word is in the data structure. A word could contain the dot character '.' to represent any one letter. */
    bool search(string word) {
        return helper(word,root);
    }
    bool helper(string word,Tree *r){
       
        Tree *p=r;
        // cout<<p->have;
        for(int i=0;i<word.size();i++){
            if(word[i]=='.'){
                
                bool res=false;
                for(int j=0;j<26;j++){
                    if(p->leaf[j]!=NULL)
                        // helper(word.substr(i+1),p->leaf[j]);
                        res=res||helper(word.substr(i+1),p->leaf[j]);
                    if(res)
                        return res;
                }
                return res;
                // return false;
            }
            if(p->leaf[word[i]-'a']==NULL)
                return false;
            else
                p=p->leaf[word[i]-'a'];
        }
        return p->have;
    }
};

/**
 * Your WordDictionary object will be instantiated and called as such:
 * WordDictionary* obj = new WordDictionary();
 * obj->addWord(word);
 * bool param_2 = obj->search(word);
 */
```
