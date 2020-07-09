```cpp
class Solution {
public:
    int computeArea(int A, int B, int C, int D, int E, int F, int G, int H) {
        int re=(long)((C-A)*(D-B))+(long)((G-E)*(H-F));
        int x=abs((long)E-A)+abs((long)G-C);
        int y=abs((long)(F-B))+abs((long)(H-D));
        int tempx=G-E+C-A;
        int tempy=D-B+H-F;
        if(tempx<=x ||tempy<=y)
            return re;
        else
            return re-((long)(tempx-x)*(tempy-y))/4;
    }
};
```