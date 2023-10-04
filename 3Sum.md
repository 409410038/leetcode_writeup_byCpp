## **15. 3Sum**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/02/2023 12:51| 118 ms |24.9 MB	| Accepted |

```
class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
    int length = nums.size();
    int exist_indx[200001];
    vector<vector<int>> answer;
    sort(nums.begin(), nums.end());
    for (int i = 0; i < 200001; i++)  exist_indx[i] = -1;
    for (int i = 0; i < length; i++)
    {
        if (nums[i] >= 0)
        {
            exist_indx[nums[i]] = i;
        }
    }
    for (int i = 0; i < length; i++)
    {
        int sum = 0;
        if (nums[i] > 0)  break;
        if (i > 0 && nums[i] == nums[i-1]) continue;
        for (int j = i + 1; j < length; j++)
        {
            sum = nums[i] + nums[j];
            if (sum > 0)  break;
            if (exist_indx[sum*-1] != -1 && exist_indx[sum*-1] > j)
            {
                if (answer.size() != 0)
                {
                    if (nums[i] != answer[answer.size()-1][0] || nums[j] != answer[answer.size()-1][1])
                    {
                        answer.push_back({nums[i], nums[j], sum*-1});
                    }
                }
                else  answer.push_back({nums[i], nums[j], sum*-1});
                
            }
        }
    }
    return answer;
    }
};
```

