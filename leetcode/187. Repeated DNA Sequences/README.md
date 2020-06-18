```cpp
class Solution {
public:
    vector<string> findRepeatedDnaSequences(string s) {
        vector<string> res;
        if (s.size() <= 10) return res;
        int mask = 0x7ffffff, cur = 0;
        unordered_map<int, int> m;
        for (int i = 0; i < 9; ++i) {
            cur = (cur << 3) | (s[i] & 7);
        }
        for (int i = 9; i < s.size(); ++i) {
            cur = ((cur & mask) << 3) | (s[i] & 7);
            if (m.count(cur)) {
                if (m[cur] == 1) res.push_back(s.substr(i - 9, 10));
                ++m[cur]; 
            } else {
                m[cur] = 1;
            }
        }
        return res;
    }
};
```
# this one is better
```cpp
class Solution {
public:
    vector<string> findRepeatedDnaSequences(string s) {
        unordered_set<string> s1,ans;
        vector<string> res;
        if(s.size()<10)
            return res;
        for(int i=0;i<s.size()-9;i++){
            string sub=s.substr(i,10);
            if(s1.count(sub) && !ans.count(sub)){
                ans.insert(sub);
                res.push_back(sub);
                
            }else{
                
                s1.insert(sub);
            }
        }
        return res;
    }
};
```

# 两个set空间占用比map小？