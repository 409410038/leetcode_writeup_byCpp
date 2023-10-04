## **227. Basic Calculator II**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/12/2023 15:04| 28 ms | 11.8 MB | Accepted |

```
class Solution {
public:
    int calculate(string s) {
        queue<int> nums;
        queue<char> punct;
        int n1 = 0, n2 = 0;
        for (int i = 0; i < s.size(); ) {
            if (s[i] == ' ')  i++;
            else if (isdigit(s[i])) {
                n1 *= 10;
                n1 += s[i] - '0';
                i++;
            }
            else {
                if (s[i] == '*') {
                    i++;
                    while (s[i] == ' ') i++;
                    while (isdigit(s[i])) {
                        n2 *= 10;
                        n2 += s[i] - '0';
                        i++;
                    }
                    n1 = n1 * n2;
                    n2 = 0;
                }
                else if (s[i] == '/') {
                    i++;
                    while (s[i] == ' ') i++;
                    while (isdigit(s[i])) {
                        n2 *= 10;
                        n2 += s[i] - '0';
                        i++;
                    }
                    n1 = n1 / n2;
                    n2 = 0;
                }
                else {
                    nums.push(n1);
                    n1 = 0;
                    punct.push(s[i]);
                    i++;
                }
            }
        }
        nums.push(n1);
        n1 = nums.front(), n2 = 0;
        nums.pop();
        while (!punct.empty()) {
            char op = punct.front();
            punct.pop();
            if (op == '+') {
                n2 = nums.front();
                nums.pop();
                n1 = n1 + n2;
            }
            else if (op == '-') {
                n2 = nums.front();
                nums.pop();
                n1 = n1 - n2;
            }
        }

        return n1;
    }
};
```

