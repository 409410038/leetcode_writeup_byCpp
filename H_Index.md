## **274. H-Index**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/14/2023 23:05	|818 ms | 8.7 MB| Accepted |

```
class Solution {
public:
    int hIndex(vector<int>& citations) {
        
        for (int i = citations.size(); i >= 0; i --) {
            citations.push_back(i);
            sort(citations.begin(), citations.end());
            vector<int>::iterator it = find(citations.begin(), citations.end(), i);
            if (citations.end()-it > i) {
                return i;
            }
            citations.erase(it);
        }
        return -1;
    }
};
```

