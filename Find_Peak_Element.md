## **162. Find Peak Element**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/04/2023 19:10	| 	3 ms | 8.8 MB	 | Accepted |

```
class Solution {
public:
    int findPeakElement(vector<int>& nums) {
        if (nums.size() == 1 || nums[0] > nums[1])  return 0;
        if (nums[nums.size()-1] > nums[nums.size()-2])  return nums.size()-1;
        for (int i = 1; i < nums.size()-1; i++) {
            if (nums[i] > nums[i-1] && nums[i] > nums[i+1])  return i;
        }
        return -1;
    }
};
```

