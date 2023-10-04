## **28. Find the Index of the First Occurrence in a String**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/02/2023 14:17	| 4 ms |6.1 MB	| Accepted |

```
class Solution {
public:
    int strStr(string haystack, string needle) {
        int indx = -1;
        for (int i = 0; i < haystack.size(); i++)
        {
            for (int j = 0; j < needle.size(); j++)
            {
                if (haystack[i+j] != needle[j])  break;
                if (j == needle.size()-1)
                {
                    return i;
                }
            }
        }
        return -1;

    }
};
```

