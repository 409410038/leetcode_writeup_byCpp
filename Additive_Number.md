## **306. Additive Number**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/21/2023 20:45|0 ms | 6.1 MB| Accepted |

```
class Solution {
public:
    bool isAdditiveNumber(string num) {
        long long n3 = 0, power3 = 1;
        long long n1 = 0, power1 = 1;
        long long n2 = 0, power2 = 1;
        long long tmp, tmp_pos, tmp_pow;
        bool flag = false;
        for (int i = num.size()-1; i >= 0; i--) {
            if (flag) {
                n1 = n1 + (num[i]-'0') * power1;
                power1 *= 10;
                if (power1 >= 1000000000000000000)  break;
                if (num[i]-'0' == 0 && n1 != 0)  continue;
                if (n3 - n2 == n1) {
                    cout << n1 << endl;
                    n3 = n2, n2 = n1;
                    n1 = 0, power1 = 1;
                }
                else if (i == 0) {
                    flag = false;
                    i = tmp_pos, power3 = tmp_pow, n3 = tmp;
                }

            }
            else {
                n3 = n3 + (num[i]-'0') * power3;
                power3 *= 10;
                if (power3 >= 1000000000000000000)  break;
                if (num[i] == '0' && n3 != 0)  continue;
                // now i need to find the two number, their sum is equal to n3
                n2 = 0, power2 = 1;
                for (int j = i-1; j >= 1; j--) {  // n2
                    n2 = n2 + (num[j]-'0') * power2;
                    power2 *= 10;
                    if (power2 >= 1000000000000000000)  break;
                    if (num[j]-'0' == 0 && n2 != 0)  continue;
                    n1 = 0, power1 = 1;
                    for (int k = j-1; k >= 0; k--) { // n1
                        n1 = n1 + (num[k]-'0') * power1;
                        power1 *= 10;
                        if (power1 >= 1000000000000000000)  break;
                        if (num[k]-'0' == 0 && n1 != 0)  continue;
                        if (n1 + n2 == n3) {
                            cout << n1 << ' ' << n2 << endl;
                            flag = true;
                            tmp = n3, tmp_pos = i, tmp_pow = power3;
                            i = k;
                            n3 = n2, n2 = n1;
                            n1 = 0, power1 = 1;
                            break;
                        }
                    }
                    if (flag) break;
                }
                //if (i == 0)  return false;
            }
        }
        if (flag)  return true;
        return false;
    }
};
```

