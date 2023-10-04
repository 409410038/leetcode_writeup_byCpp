## **221. Maximal Square**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/11/2023 18:08| 179 ms | 19 MB | Accepted |

```
class Solution {
public:
    int maximalSquare(vector<vector<char>>& matrix) {
        int maxsquare = 0;
        int square[300][300];
        int flag = 1;
        for (int i = 0; i < matrix.size(); i++) {
            for (int j = 0; j < matrix[0].size(); j++) {
                if (matrix[i][j] == '1')  square[i][j] = 1;
                else  square[i][j] = 0;
            }
        }
        for (int i = 0; i < matrix.size(); i++) {
            if (matrix.size()-i < maxsquare)  break;
            for (int j = 0; j < matrix[0].size(); j++) {
                if (matrix[0].size()-j < maxsquare)  break;
                if (square[i][j] > 0) {
                    flag = 1;
                    int length = square[i][j];   
                    //cout << square[i][j] << endl; 
                    while (flag) {
                        if (i+length >= matrix.size() || j+length >= matrix[0].size())  break;
                        for (int a = 0; a <= length; a++) {
                            if (matrix[i+length][j+a] == '0' || matrix[i+a][j+length] == '0') {
                                flag = 0;
                                break;
                            }
                        }
                        if (flag)  length++;
                    }
                    for (int a = 0; a < length; a++) {
                        for (int b = 0; b < length; b++) {
                            square[i+a][j+b] = max(length - max(a, b), square[i+a][j+b]);
                        }
                    }
                    if (length > maxsquare)  maxsquare = length;
                    //cout << length << endl;
                }
            }
        }
        return maxsquare*maxsquare;
    }
};
```

