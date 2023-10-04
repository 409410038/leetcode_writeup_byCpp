## **331. Verify Preorder Serialization of a Binary Tree**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
|03/07/2023 23:37|0 ms |7.5 MB| Accepted |

```
class Solution {
public:
    class Node {
    public:
        bool left = false;
        bool right = false;
    };
    bool isValidSerialization(string preorder) {
        // preorder: visit->left->right
        
        stack<Node*> nodes;
        Node* tmp = nullptr;
        bool start = false;
        for (int i = 0; i < preorder.size(); i++) {
            if (isdigit(preorder[i])) {
                while (isdigit(preorder[i]))  i++;
                if (start == false) {
                    tmp = new Node();
                    nodes.push(tmp);
                    start = true;
                }
                else if (nodes.empty()) {
                    return false;
                }
                else {
                    if (nodes.top()->left == false)  nodes.top()->left = true;
                    else if (nodes.top()->right == false) {
                        delete (nodes.top());
                        nodes.pop();
                    } 
                    else  return false;
                    tmp = new Node();
                    nodes.push(tmp);
                }
                i--;
            }
            else if (preorder[i] == ',')  continue;
            else if (preorder[i] == '#') {
                if (start == false) {
                    start = true;
                }
                else if (nodes.empty())  return false;
                else {
                    if (nodes.top()->left == false)  nodes.top()->left = true;
                    else if (nodes.top()->right == false) {
                        delete (nodes.top());
                        nodes.pop();
                    }
                }
            }
            else {
                cout << "something wrong" << endl;
            }
        }
        if (!nodes.empty())  return false;
        else  return true;
    }
};
```

