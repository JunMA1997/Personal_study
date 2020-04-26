``` cpp
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        // if(s.size()<=1)
        //     return s.size();
        vector<int> record(128);
        int temp=0;
        int longest=0;
        for(int i = 0; i < s.size(); i++){    
            // cout<<temp<<endl;        
            if(record[s[i]]==0){
                record[s[i]] = i+1;
                temp++;
                // cout<<s<<endl;
            }
            else{
                if(i-record[s[i]]-1<temp){
                    //repeating because this word
                    
                    if(longest<temp){
                        longest=temp;
                    }
                    temp = i-record[s[i]]+1;
                    record[s[i]]=i+1;
                }
                else
                {
                    //not this word repeating
                    record[s[i]] = i+1;
                    temp++;
                }
            }
        }
        if(longest<temp){
            longest=temp;
        }
        return longest;
    }
};
```
# use O(N) space, O(N)time, record last appear position