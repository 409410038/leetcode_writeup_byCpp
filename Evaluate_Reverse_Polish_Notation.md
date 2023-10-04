## **150. Evaluate Reverse Polish Notation**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/04/2023 14:46	| 0 ms | 12 MB	 | Accepted |

```
class Solution {
public:
    int evalRPN(vector<string>& tokens) {
        stack<int> nums;
        int sum = 0;
        bool flag = false;
        vector<string>::iterator it = tokens.begin();
        while (it != tokens.end()) {
            if ((*it).size()==1 && ispunct((*it)[0])) {
                int n1, n2;
                n2 = nums.top();
                nums.pop();
                n1 = nums.top();
                nums.pop();
                
                if ((*it)[0] == '+')  sum = n1 + n2;
                else if ((*it)[0] == '-')  sum = n1 - n2;
                else if ((*it)[0] == '*')  sum = n1 * n2;
                else if ((*it)[0] == '/')  sum = n1 / n2;
                nums.push(sum);
            }
            else {
                
                nums.push(stoi(*it));
            }
            it++;
        }
        if (!nums.empty())  return(nums.top());
        return sum;
    }
};
```

