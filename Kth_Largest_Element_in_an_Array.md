## **215. Kth Largest Element in an Array**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/10/2023 23:37| 107 ms | 45.5 MB | Accepted |

```
class Solution {
public:
    int findKthLargest(vector<int>& nums, int k) {
        sort(nums.begin(), nums.end());
        return nums[nums.size()-k];
    }

};
```

