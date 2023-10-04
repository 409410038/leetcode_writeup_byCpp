## **199. Binary Tree Right Side View**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/07/2023 15:21	| 0 ms | 12 MB	 | Accepted |

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
    vector<int> answer;
    int looked[100];
    void recursion(TreeNode* node, int layer) {
        if (node == nullptr)  return;
        if (looked[layer] == 0) {
            answer.push_back(node->val);
            looked[layer] = 1;
        }
        recursion(node->right, layer+1);
        recursion(node->left, layer+1);
    }
    vector<int> rightSideView(TreeNode* root) {
        for (int i = 0; i < 100; i++) {
            looked[i] = 0;
        }
        recursion(root, 0);

        return answer;
    }
};
```

