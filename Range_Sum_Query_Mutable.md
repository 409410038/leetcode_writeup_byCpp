## **307. Range Sum Query - Mutable**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/22/2023 22:42|573 ms | 172.8 MB| Accepted |

```
class NumArray {
public:
    vector<int> mynums;
    int sum[30001];
    int min_update = -1;
    int max_update = -1;
    int update_bias = 0;
    NumArray(vector<int>& nums) {
        mynums = nums;
        sum[0] = nums[0];
        for (int i = 1; i < nums.size(); i++) {
            sum[i] = sum[i-1] + nums[i];
        }
    }
    
    void update(int index, int val) {
        if (min_update == -1 || index < min_update) {
            min_update = index;
        }
        if (max_update == -1 || index > max_update) {
            max_update = index;
        }
        update_bias += val - mynums[index];
        mynums[index] = val;
        return;
    }
    
    int sumRange(int left, int right) {
        if (left == right)  return mynums[left];
            
        if (min_update != -1) {
           
            if (max_update <= right && min_update >= left) {
                if (left == 0)  return sum[right] + update_bias;
                else  return sum[right] - sum[left-1] + update_bias;
            }
            else {
                for (int i = 0; i < mynums.size(); i++) {
                    if (i == 0)  sum[i] = mynums[i];
                    else  sum[i] = sum[i-1] + mynums[i];
                }
                min_update = -1;
                max_update = -1;
                update_bias = 0;
            }
        }
        
        if (left == 0)  return sum[right];
        
        return sum[right] - sum[left-1];
    }
};

/**
 * Your NumArray object will be instantiated and called as such:
 * NumArray* obj = new NumArray(nums);
 * obj->update(index,val);
 * int param_2 = obj->sumRange(left,right);
 */
```

