## **260. Single Number III**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/13/2023 22:41	|11 ms | 10.1 MB| Accepted |

```
class Solution {
public:
    vector<int> singleNumber(vector<int>& nums) {
        vector<int> answer;
        sort(nums.begin(), nums.end());
        int count = 1;
        for (int i = 1; i < nums.size(); i++) {
            if (nums[i] == nums[i-1]) {
                count ++;
            }
            else {
                if (count == 1)  answer.push_back(nums[i-1]);
                count = 1;
            } 
        }
        if (count == 1)  answer.push_back(nums[nums.size()-1]);
        return answer;
    }
};
```

