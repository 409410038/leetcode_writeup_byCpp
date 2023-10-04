## **165. Compare Version Numbers**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/05/2023 14:09	| 	4 ms | 6.5 MB	 | Accepted |

```
class Solution {
public:
    int compareVersion(string version1, string version2) {
        int pos1 = 0, pos2 = 0;
        size_t p1, p2;
        int v1, v2;
        while (pos1 < version1.size() || pos2 < version2.size()) {
            if (pos1 >= version1.size())  v1 = 0;
            else {
                v1 = stoi(&version1[pos1], &p1);
                pos1 += p1 + 1;
            } 
            if (pos2 >= version2.size())  v2 = 0;
            else {
                v2 = stoi(&version2[pos2], &p2);
                pos2 += p2 + 1;
            } 

            if (v1 > v2)  return 1;
            else if (v1 < v2)  return -1;
        }
        return 0;
    }
};
```

