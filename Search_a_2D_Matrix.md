## **74. Search a 2D Matrix**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/03/2023 14:44	| 10 ms | 9.6 MB | Accepted |

```
class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
        int left, right, mid;
        left = 0, right = matrix.size()-1;
        while (left < right) {
            mid = (left + right) / 2;
            if (matrix[mid][0] == target)  return true;
            else if (target > matrix[mid][0]) {
                if (target >= matrix[mid+1][0])  left = mid + 1;
                else if (target < matrix[mid+1][0]) {
                    left = mid;
                    right = mid;
                }
            }
            else if (target < matrix[mid][0])  right = mid - 1;
        }
        int indx = left;
        left = 0, right = matrix[0].size()-1;
        while (left <= right) {
            mid = (left + right) / 2;
            if (left == right) {
                if (matrix[indx][mid] == target) return true;
                break;
            }
            if (matrix[indx][mid] == target)  return true; 
            else if (matrix[indx][mid] < target)  left = mid + 1;
            else if (matrix[indx][mid] > target)  right = mid - 1;
        }
        
        return false;
    }
};
```

