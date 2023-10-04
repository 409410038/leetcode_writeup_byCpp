## **322. Coin Change**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
|02/28/2023 20:54|90 ms |9.9 MB| Accepted |

```
class Solution {
public:
    int coinChange(vector<int>& coins, int amount) {
        int min_cnt[10001];
        min_cnt[0] = 0;
        for (int i = 1; i < 10001; i++) {
            min_cnt[i] = -1;
        }
        
        for (int i = 1; i <= amount; i++) {
            int minn = 10001;
            for (int j = 0; j < coins.size(); j++) {
                if (coins[j] > i)  continue;
                if (min_cnt[i - coins[j]] != -1 && min_cnt[i - coins[j]] + 1 < minn)  
                    minn = min_cnt[i - coins[j]] + 1; 
            }
            if (minn == 10001)  min_cnt[i] = -1;
            else  min_cnt[i] = minn;
        }
        return min_cnt[amount];
    }
};
```

