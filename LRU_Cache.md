## **146. LRU Cache**

| Time Submitted | Runtime | Memory Usage | Status|
| -------------- |  ------- | -------------| --|
| 02/03/2023 20:40	| 465 ms | 163.8 MB | Accepted |

```
class LRUCache {
public:
    deque<int> recently_used;
    int cache[10001][2];
    int c;
    int used = 0;
    LRUCache(int capacity) {
        for (int i = 0; i < 10001; i++) {
            cache[i][0] = -1;
            cache[i][1] = 0;  //used_count
        }
        c = capacity;
        used = 0;
    }
    
    int get(int key) {
        if (cache[key][0] != -1) {
            cache[key][1]++;
            recently_used.push_back(key);
        }
        return cache[key][0];
    }
    
    void put(int key, int value) {
        if (cache[key][0] == -1) {
            if (used < c) {
                used++;
            }
            else {
                while (cache[recently_used.front()][1] > 1) {
                    cache[recently_used.front()][1]--;
                    recently_used.pop_front();
                }
                cache[recently_used.front()][0] = -1;
                cache[recently_used.front()][1]--;
                recently_used.pop_front();
            }
        }
        cache[key][0] = value;
        cache[key][1]++;
        recently_used.push_back(key);
    }
};

/**
 * Your LRUCache object will be instantiated and called as such:
 * LRUCache* obj = new LRUCache(capacity);
 * int param_1 = obj->get(key);
 * obj->put(key,value);
 */
```

