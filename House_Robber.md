## **198. House Robber**
#### Problem Description Link: https://leetcode.com/problems/house-robber/

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/07/2023 14:11| 2 ms | 7.6 MB	 | Accepted |

### Intuition
The only constraint is whether the neighbor has been robbed. So you don't need to find out entire robbing pattern. Just consider the current one rob or not.

### Approach
If the current solution satisfies the constraint and you calculate the new solution under the constraint, all the solutions will satisfy the constraint.

#### step 1: Initialize the current solution. (No.0 house included only)

#### step 2: Scan all the items in nums in sequence.
If the previous position in the solution is not the current one's neighbor, just put the current house into solution. Else if the last solution + the current house > the current solution, put the current house into solution.

#### step 3: Update the last solution for future recovering and the current solution.

### Complexity
Time complexity: $O(n)$

Space complexity:  $O(1)$
```
class Solution {
public:
    int rob(vector<int>& nums) {
        int last = 0, cur = 0;
        int prev_pos = 0;
        cur = nums[0];
        for (int i = 1; i < nums.size(); i++) {
            if (i > prev_pos+1) {
                last = cur;
                cur = cur + nums[i];
                prev_pos = i;
            }
            else if (last+nums[i] > cur) {
                int tmp = cur;
                cur = last + nums[i];
                prev_pos = i;
                last = tmp;
            }
            
        }
        return cur;
    }
};
```

