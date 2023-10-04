## **287. Find the Duplicate Number**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/18/2023 22:03|170 ms | 61.3 MB| Accepted |

```
class Solution {
public:
    int findDuplicate(vector<int>& nums) {
        int low = 1, high = nums.size()-1;
        while (low < high) {
            int mid = (low + high) / 2;
            int cnt = 0;
            for (int i = 0; i < nums.size(); i++) {
                if (nums[i] <= mid)  cnt ++;
            }
            if (cnt <= mid)  low = mid+1;
            else  high = mid;
        }
        
        return low;
    }
};
```

