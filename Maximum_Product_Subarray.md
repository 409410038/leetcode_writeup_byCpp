## **152. Maximum Product Subarray**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/04/2023 17:58	| 	7 ms | 14.4 MB	 | Accepted |

```
class Solution {
public:
    int maxProduct(vector<int>& nums) {
        vector<int> product;
        int max = nums[0], min = nums[0] , max_indx = 0, min_indx = 0;
        bool zero = false;
        product.push_back(nums[0]);
        for (int i = 1; i < nums.size(); i++) {
            if (product[i-1] == 0)  product.push_back(nums[i]);
            else  product.push_back(product[i-1]*nums[i]);
            if (product[i] == 0) {
                zero = true;
                continue;
            }
            if (max <= product[i] || max == 0)  max = product[i], max_indx = i;
            if (min >= product[i] || min == 0)  min = product[i], min_indx = i;
        }
        cout << max << min<<endl;
        int tmp = max;
        for (int i = max_indx-1; i >= 0; i--) {
            if (product[i] == 0)  break;
            if (tmp/product[i] > max) max = tmp / product[i];
        }
        tmp = min;
        for (int i = min_indx-1; i >= 0; i--) {
            if (product[i] == 0)  break;
            if (tmp/product[i] > max) max = tmp / product[i];
        }
        if (zero && max < 0)  max = 0;
        return max;
    }
};
```

