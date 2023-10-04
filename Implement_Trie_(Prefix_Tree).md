## **208. Implement Trie (Prefix Tree)**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/07/2023 15:40	| 458 ms | 	24.2 MB | Accepted |

```
class Trie {
public:
    vector<string> words;
    Trie() {

    }
    
    void insert(string word) {
        words.push_back(word);
    }
    
    bool search(string word) {
        for (int i = 0; i < words.size(); i++) {
            if (words[i] == word)  return true;
        }
        return false;
    }
    
    bool startsWith(string prefix) {
        for (int i = 0; i < words.size(); i++) {
            if (words[i].find(prefix) == 0)  return true;
        }
        return false;
    }
};

/**
 * Your Trie object will be instantiated and called as such:
 * Trie* obj = new Trie();
 * obj->insert(word);
 * bool param_2 = obj->search(word);
 * bool param_3 = obj->startsWith(prefix);
 */
```

