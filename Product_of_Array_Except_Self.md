## **238. Product of Array Except Self**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/13/2023 22:08	|22 ms |  24.8 MB| Accepted |

```
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        int prefix[100000];
        int suffix[100000];
        for (int i = 0; i < nums.size(); i++) {
            if (i == 0)  prefix[i] = nums[i];
            else  prefix[i] = prefix[i-1]*nums[i];
        }
        for (int i = nums.size()-1; i >= 0; i--) {
            if (i == nums.size()-1)  suffix[i] = nums[i];
            else  suffix[i] = suffix[i+1]*nums[i];
        }
        for (int i = 0; i < nums.size(); i++) {
            if (i == 0)  nums[i] = suffix[i+1];
            else if (i == nums.size()-1)  nums[i] = prefix[i-1];
            else {
                nums[i] = prefix[i-1] * suffix[i+1];
            }
            
        }
        
        return nums;
    }
};
```

