## **139. Word Break**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/03/2023 18:48	| 6 ms | 7.6 MB | Accepted |

```
class Solution {
public:
    bool wordBreak(string s, vector<string>& wordDict) {
        int find[1001];
        int invalid[1001];
        for (int i = 0; i < wordDict.size(); i++) {
            size_t indx = s.find(wordDict[i]);
            if (indx != string::npos)  find[i] = (int)indx;
            else  find[i] = -1;
            invalid[i] = 0;
        }
        int start = 0;
        int last_failed = -1;
        size_t indx;
        vector<int> route;
        vector<int> unvalid;
        while (start < s.size()) {
            if (last_failed != -1 && start > last_failed) {
                while (!unvalid.empty()) {
                    invalid[unvalid.back()] = 0;
                    unvalid.pop_back();
                }
            }
            for (int j = 0; j <= wordDict.size(); j++) {
                if (j == wordDict.size()) {
                    if (route.empty())  return false;
                    int last = route.back();
                    unvalid.push_back(last);
                    route.pop_back();
                    if (start > last_failed)  last_failed = start;
                    start = start - wordDict[last].size();
                    invalid[last] = 1;
                    break;
                }
                if (invalid[j] == 1)  continue;
                if (find[j] == -1)  continue;
                else if (find[j] == start) {
                    start = start + wordDict[j].size();
                    route.push_back(j);
                    break;
                }
                else {
                    indx = s.find(wordDict[j], start);
                    if (indx == start) {
                        start = start + wordDict[j].size();
                        route.push_back(j);
                        break;
                    }
                }
            }
        }

        return true;
        
    }
};
```

