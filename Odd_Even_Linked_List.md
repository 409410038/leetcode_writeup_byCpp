## **328. Odd Even Linked List**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
|003/02/2023 23:39|18 ms |10.5 MB| Accepted |

```
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* oddEvenList(ListNode* head) {
        ListNode* even = nullptr;
        ListNode* odd = nullptr;
        ListNode* even_head = nullptr;
        ListNode* node = head;
        int cnt = 1;
        while(node != nullptr) {
            if (cnt%2 == 0) {
                if (even_head == nullptr) {
                    even_head = node;
                    even = node;
                }
                else {
                    even->next = node;
                    even = node;
                }
            }
            else {
                if (odd == nullptr)  odd = node;
                else {
                    odd->next = node;
                    odd = node;
                }
            }
            node = node->next;
            cnt ++;
        }
        if (even != nullptr)   even->next = nullptr;
        if (odd != nullptr)   odd->next = even_head;
        return head;
    }
};
```

