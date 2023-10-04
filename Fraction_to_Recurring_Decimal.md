## **166. Fraction to Recurring Decimal**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/05/2023 16:30	| 	0 ms | 7.5 MB	 | Accepted |

```
class Solution {
public:
    string fractionToDecimal(int numerator, int denominator) {
        string answer;
        map<long long, int> pattern;
        long long numerator1 = numerator, denominator1 = denominator;
        if (numerator1 == 0)  return "0";
        if (numerator1 * denominator1 < 0)  answer.push_back('-');
        numerator1 = abs(numerator1), denominator1 = abs(denominator1);
        
        answer = answer + to_string(numerator1/denominator1);
        numerator1 = numerator1 % denominator1;
        if (numerator1 != 0)  answer.push_back('.');
        
        while (numerator1 != 0) {
            numerator1 *= 10;
            if (pattern.find(numerator1) == pattern.end()) {
                pattern.insert(pair<long long, int>(numerator1, answer.size()));
            }
            else {
                int pos = pattern.find(numerator1)->second;
                answer.insert(pos, 1, '(');
                answer.push_back(')');
                break;
            }
            answer = answer + to_string(numerator1/denominator1);
            numerator1 = numerator1 % denominator1;
        }
        return answer;
    }
};
```

