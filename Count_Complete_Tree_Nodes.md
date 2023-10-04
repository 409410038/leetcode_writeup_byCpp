## **222. Count Complete Tree Nodes**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/11/2023 18:17| 33 ms | 30.9 MB | Accepted |

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
    int count = 0;
    void trival(TreeNode* root) {
        if (root == nullptr)  return;
        count++;
        trival(root->left);
        trival(root->right);
        return;
    }
    int countNodes(TreeNode* root) {
        trival(root);
        return count;
    }
};
```

