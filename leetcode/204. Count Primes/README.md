```cpp
class Solution {
public:
    int countPrimes(int n)
    {
        bool prime[n+1];
        memset(prime,true,sizeof(prime));

        for(int i=2;i*i<=n;i++)
        {
            if(prime[i])
            {
                for(int j=i*i;j<=n;j+=i)
                    prime[j]=false;
            }
        }
        int cnt=0;
        for(int k=2;k<n;k++)
        {
            if(prime[k])
             cnt++;
        }
        return cnt;
    }
};
```
# sometimes, when we already know how much we need, using array list is better than vector.
* vector会天然降低程序效率