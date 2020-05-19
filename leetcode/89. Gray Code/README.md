```cpp
class Solution {
public:
    vector<int> grayCode(int n) {
        vector<int> res;
        for(int i=0;i<pow(2,n);i++){
            res.push_back((i>>1)^i);
        }
        return res;
    }
};
```
|order|number|greycode|
|0|000|000|
|1|001|001|
|2|010|011|
|3|011|010|
|4|100|110|
|5|101|111|
|6|110|101|
|7|111|100|
|8|1000|1100|
|9|1001|1101|
|10|1010|1111|
|11|1011|1110|
|12|1100|1010|