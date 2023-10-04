## **204. Count Primes**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/07/2023 15:30	| 339 ms | 28 MB | Accepted |

```
class Solution {
public:
    int countPrimes(int n) {
        int nums[5000001];
        int count = 0;
        for (int i = 0; i < n; i++) {
            nums[i] = 1;
        }
        for (int i = 2; i < n; i++) {
            if (nums[i] == 1) {
                count ++;
                for (int j = 2; j <= n/i; j++) {
                    nums[i*j] = 0;
                }
            }
        }
        return count;
    }
};
```

