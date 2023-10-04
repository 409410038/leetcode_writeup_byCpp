## **229. Majority Element II**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/12/2023 15:17| 16 ms | 16.1 MB | Accepted |

```
class Solution {
public:
    vector<int> majorityElement(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        vector<int> answer;
        int count = 1, m = nums.size() / 3;
        for (int i = 1; i < nums.size(); i++) {
            if (nums[i] != nums[i-1]) {
                if (count > m)  answer.push_back(nums[i-1]);
                count = 1;
            }
            else  count ++;
        }
        if (count > m)  answer.push_back(nums.back());
        return answer;
    }
};
```

