## **33. Search in Rotated Sorted Array**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/02/2023 14:26	| 0 ms | 11.2 MB| Accepted |

```
class Solution {
public:
    int search(vector<int>& nums, int target) {
        vector<int>::iterator it = find(nums.begin(), nums.end(), target);
        if (it == nums.end())  return -1;
        else  return it-nums.begin();
    }
};
```

