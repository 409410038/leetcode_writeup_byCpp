## **172. Factorial Trailing Zeroes**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/05/2023 16:39	| 	0 ms | 5.9 MB	 | Accepted |

```
class Solution {
public:
    int trailingZeroes(int n) {
        int count = 0;
        while (n != 0) {
            count += n / 5;
            n /= 5;
        }
        return count;
    }
};
```

