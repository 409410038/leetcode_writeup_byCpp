## **209. Minimum Size Subarray Sum**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/10/2023 17:10| 31 ms | 28.3 MB | Accepted |

```
class Solution {
public:
    int minSubArrayLen(int target, vector<int>& nums) {
        int sum = 0;
        int left = 0, right = 0;
        int last_pos = 0, min_length = 10000000;
        if (nums[0] >= target)  return 1;
        for (int i = 0; i < nums.size(); i++) {
            sum += nums[i];
            if (sum >= target) {
                while (left < i) {
                    if (sum - nums[left] >= target) {
                        sum -= nums[left];
                        left ++;
                    }
                    else  break;
                }
                if (i - left + 1 < min_length)  min_length = i - left + 1;
            }
        }
        if (min_length == 10000000)  return 0;
        return min_length;
    }
};
```

