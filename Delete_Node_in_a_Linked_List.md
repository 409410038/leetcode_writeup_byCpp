## **237. Delete Node in a Linked List**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/13/2023 20:57| 9 ms | 7.7 MB | Accepted |

```
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    void deleteNode(ListNode* node) {
        node->val = node->next->val;
        node->next = node->next->next;
    }
};
```

