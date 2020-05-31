# this solution i think is not good but i cant get greater solution
```cpp
class Solution {
public:
    int ladderLength(string beginWord, string endWord, vector<string>& wordList) {
        for(int i=0;i<=wordList.size();i++){
            if(i==wordList.size())
                return 0;
            if(endWord==wordList[i]){
                break;
            }
        }
        unordered_set<string> wordSet(wordList.begin(), wordList.end());
        unordered_map<string, int> pathCnt{{{beginWord, 1}}};
        queue<string> q{{beginWord}};
        while(!q.empty()){
            string word=q.front();
            q.pop();
            for(int i=0;i<word.size();i++){
                string newword=word;
                for(char ch='a';ch<='z';ch++){
                    newword[i]=ch;
                    if(wordSet.count(newword) && newword==endWord) 
                        return pathCnt[word] + 1;
                    if(wordSet.count(newword) && !pathCnt.count(newword)){
                        q.push(newword);
                        pathCnt[newword] = pathCnt[word] + 1;
                    }
                }
            }
            
        }
        return 0;
    }
};
```