## **235. Lowest Common Ancestor of a Binary Search Tree**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/12/2023 23:40| 30 ms | 23.4 MB | Accepted |

```
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */

class Solution {
public:
    vector<TreeNode*> route;
    void explore(TreeNode* root) {
        if (root == nullptr)  return;
        route.push_back(root);
        explore(root->left);
        explore(root->right);
        return;
    }
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        vector<TreeNode*> route_p;
        vector<TreeNode*> route_q;
        TreeNode* tmp = root;
        while (root != nullptr) {
            route_p.push_back(root);
            if (root->val > p->val)  root = root->left;
            else if (root->val < p->val)  root = root->right;
            else  break;
        }
        root = tmp;
        while (root != nullptr) {
            route_q.push_back(root);
            if (root->val > q->val)  root = root->left;
            else if (root->val < q->val)  root = root->right;
            else  break;
        }
        for (int i = route_p.size()-1; i >= 0; i--) {
            if (find(route_q.begin(), route_q.end(), route_p[i]) != route_q.end())  return route_p[i];
        }
        return nullptr;
    }
};
```

