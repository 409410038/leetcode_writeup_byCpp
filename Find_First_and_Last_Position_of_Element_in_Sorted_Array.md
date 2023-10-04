## **34. Find First and Last Position of Element in Sorted Array**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/02/2023 19:51	| 12 ms | 13.7 MB | Accepted |

```
class Solution {
public:
    int L = -1, R = -1;
    void recursive(vector<int>& nums, int target, int left, int right)
    {
        if (L != -1 && R != -1)  return;
        if (right < left)  return;
        int mid = (left+right)/2;
        if (nums[mid] < target)  left = mid;
        else if (nums[mid] > target) right = mid;
        else
        {
            if (mid == 0)  L = mid;
            else if (nums[mid-1] != target)  L = mid;
            if (mid == nums.size()-1)  R = mid;
            else if (nums[mid+1] != target)  R = mid;
        }
        recursive(nums, target, left, mid-1);
        recursive(nums, target, mid+1, right);
    }
    vector<int> searchRange(vector<int>& nums, int target) {
        recursive(nums, target, 0, nums.size()-1);
        return {L, R};
    }
};
```

