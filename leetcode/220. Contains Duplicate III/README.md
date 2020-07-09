```cpp
typedef long long LL;
class Solution {
public:
	bool containsNearbyAlmostDuplicate(vector<int>& nums, int k, int t) {
		if (k <= 0 || t < 0) return false;
		set<LL> order;
		for (int i = 0; i < nums.size(); i++) {
			auto it = order.lower_bound((LL)nums[i] - (LL)t);
			if (it != order.end() && *it <= (LL)nums[i] + (LL)t)
				return true;
			if (i >= k) order.erase(nums[i - k]);
			order.insert(nums[i]);
		}
		return false;
	}
};
```