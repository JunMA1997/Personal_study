```cpp
class Solution {
public:
    int canCompleteCircuit(vector<int>& gas, vector<int>& cost) {
        int n=gas.size();
        for(int i=0;i<n;i++){
            int temp=0;
            for(int j=0;j<n;j++){
                temp+=gas[(i+j)%n]-cost[(i+j)%n];
                if(temp<0)
                    break;
            }
            if(temp>=0)
                return i;
        }
        return -1;
    }
};
```
# easy O($$n^2$$) solution
```cpp
class Solution {
public:
    int canCompleteCircuit(vector<int>& gas, vector<int>& cost) {
        int start=0,total=0,sum=0;
        for(int i=0;i<gas.size();i++){
            total+=gas[i]-cost[i];
            sum+=gas[i]-cost[i];
            if(sum<0)
            {
                start=i+1;
                sum=0;
            }
        }
        return total<0? -1:start;
    }
};
```
# total<0 : no way
# sum<0 next station maybe a choice