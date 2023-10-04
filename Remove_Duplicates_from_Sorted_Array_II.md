## **80. Remove Duplicates from Sorted Array II**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/03/2023 15:32	| 3 ms | 10.8 MB | Accepted |

```
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        vector<int>::iterator cur_space, cur_num;
        int replace = 0;
        int count = 1;
        cur_num = nums.begin() + 1;
        cur_space = nums.end();
        while (cur_num != nums.end()) {
            if (*cur_num == *(cur_num - 1)) {
                if (replace == 1 && cur_space == nums.end()) {
                    cur_space = cur_num;
                    continue;
                }
                else if (replace == 0) {
                    replace = 1;
                    if (cur_space != nums.end()) {
                        *cur_space = *cur_num;
                        cur_space++;
                    }
                    count++;
                }
            }
            else {
                replace = 0;
                if (cur_space != nums.end()) {
                    *cur_space = *cur_num;
                     cur_space++;
                }
                count++;
            }
            cur_num++;
        }
        return count;
    }
};
```

