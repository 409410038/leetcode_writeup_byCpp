## **279. Perfect Squares**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/14/2023 23:41|110 ms | 6.1 MB| Accepted |

```
class Solution {
public:
    int numSquares(int n) {
        int mincnt[10001];
        mincnt[0] = 0;
        for (int i = 1; i <= n; i++) {
            mincnt[i] = 1000000;
        }
        for (int i = 1; i <= sqrt(n); i++) {
            mincnt[i*i] = 1;
        }
        for (int i = 2; i <= n; i++) {
            int count = 100000;
            for (int j = 1; j <= sqrt(i); j++) {
                count = min(count, mincnt[j*j] + mincnt[i - j*j]);
            }
            mincnt[i] = count;
        }
        
        return mincnt[n];
    }
};
```

