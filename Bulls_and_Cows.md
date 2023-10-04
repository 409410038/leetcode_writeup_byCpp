## **299. Bulls and Cows**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/17/2023 21:54|50 ms | 6.4 MB| Accepted |

```
class Solution {
public:
    string getHint(string secret, string guess) {
        int pair_s[1001], pair_g[1001], meet_cnt = 0, hmeet_cnt = 0;
        for (int i = 0; i < secret.size(); i++) {
            if (secret[i] == guess[i]) {
                pair_s[i] = 1;
                pair_g[i] = 1;
                meet_cnt ++;
            }
            else {
                pair_s[i] = 0, pair_g[i] = 0;
            } 
        }
        for (int i = 0; i < secret.size(); i++) {
            if (pair_s[i] == 1)  continue;
            for (int j = 0; j < guess.size(); j++) {
                if (pair_g[j] == 1 || pair_s[i] == 1)  continue;
                if (secret[i] == guess[j]) {
                    hmeet_cnt ++;
                    pair_s[i] = 1;
                    pair_g[j] = 1;
                }
            }
        }
        string answer = to_string(meet_cnt) + 'A' + to_string(hmeet_cnt) + 'B';
        return answer;

    }
};
```

