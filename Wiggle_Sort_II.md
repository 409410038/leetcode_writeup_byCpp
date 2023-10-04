## **324. Wiggle Sort II**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
|02/28/2023 22:47|27 ms |18.5 MB| Accepted |

```
class Solution {
public:
    void wiggleSort(vector<int>& nums) {
        sort(nums.begin(), nums.end(), greater<int>());
        vector<int> cnums;
        //cnums.push_back(nums[0]);
        int mid = nums.size()/2;
        int k = nums.size()%2;
        for (int i = 0; i < mid; i++) {
            cnums.push_back(nums[mid+i]);
            cnums.push_back(nums[i]); 
        }
        if (k == 1)  cnums.push_back(nums.back());
        nums = cnums;
        
    }
};
```

