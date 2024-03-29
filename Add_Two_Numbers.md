## **2. Add Two Numbers**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 11/30/2022 23:28| 47 ms |71.3 MB| Accepted |

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
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        int pre_carry = 0;
        int nxt_carry = 0;
        ListNode* l3 = new ListNode();  //header
        ListNode* p1 = l1;
        ListNode* p2 = l2;
        ListNode* p3 = l3;
        
        while (p1 != nullptr || p2 != nullptr){
            
            if (p1 != nullptr && p2 != nullptr){
                p3->val = p1->val + p2->val;
                p1 = p1->next;
                p2 = p2->next;
            }
            
            else if (p1 == nullptr){
                p3->val = p2->val;
                p2 = p2->next;
            }
            
            else if (p2 == nullptr){
                p3->val = p1->val;
                p1 = p1->next;
            }
            
            if (pre_carry != 0){
                p3->val = p3->val + 1;
            }
            if (p3->val >= 10){
                nxt_carry = 1;
                p3->val = p3->val - 10;
            }
            pre_carry = nxt_carry;
            nxt_carry = 0;
            if (p1 == nullptr && p2 == nullptr && pre_carry == 0){
                break;
            }
            p3->next = new ListNode();
            p3 = p3->next;
            
        }
        if (pre_carry != 0){
            p3->val = 1;
        }
        return l3;
    }
};
```

