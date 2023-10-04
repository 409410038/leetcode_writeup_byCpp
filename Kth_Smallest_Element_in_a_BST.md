## **230. Kth Smallest Element in a BST**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/12/2023 23:05| 16 ms | 24.2 MB | Accepted |

```
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    int count = 0, k1;
    int val = 0;
    void explore(TreeNode* root) {
        
        if (count == k1)  return;
        if (root == nullptr)  return;
        explore(root->left);
        count++;
        if (count == k1)  val = root->val;
        explore(root->right);
    }
    int kthSmallest(TreeNode* root, int k) {
        vector<TreeNode*> route;
        k1 = k;
        explore(root);
        return val;
    }
};
```

