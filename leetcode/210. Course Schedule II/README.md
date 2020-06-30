```cpp
class Solution {
public:
    vector<int> findOrder(int numCourses, vector<vector<int>>& prerequisites) {
        vector<int> res;
        vector<vector<int>> c(numCourses,vector<int>());
        vector<int> in(numCourses,0);
        for(auto &a:prerequisites){
            ++in[a[0]];
            c[a[1]].push_back(a[0]);
        }
        queue<int> q;
        for(int i=0;i<numCourses;i++){
            if(in[i]==0)
                q.push(i);
        }
        while(q.size()){
            int t=q.front();
            res.push_back(t);
            q.pop();
            for(auto &a:c[t]){
                --in[a];
                if(in[a]==0)
                    q.push(a);
            }
        }
        if(res.size()==numCourses)
            return res;
        else
            return {};
    }
};
```