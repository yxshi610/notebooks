# Algorithm
## Backtracking/DFS
1. path
2. choices
3. end

```python
result = []
def backtrack(path, choices):
  if end:
    result.add(path)
    return 
   
  for choice in choices:
    make choice
    backtrack(path, choices')
    remove choice
```

## BFS
```cpp
int BFS(Node start, Node target) {
  queue<> q, add q;
  bool<> visited, visited[q];
  
  int step = 0;
  while (!q.empty()) {
    int size = q.size();
    for (i : size) {
      cur = top, pop
      if (isTarget(cur)) return step;
      for (auto x : cur.neighbors && !visited) q.push(x);
    }
    ++step;
  }
}
```

# STL
## priority_queue
```cpp
// max_heap, push maximum
priority_queue<int, vector<int>> pq;
// min_heap, push minimum
priority_queue<int, vector<int>, greater<int>> pq;
// custom compare, note: max heap!!!
auto comp = [](ListNode* a, ListNode* b ) { return a->val < b->val; };
priority_queue<ListNode*, vector<ListNode*>, decltype(comp)> pq(comp);
```

```cpp
struct TreeNode {
    int val;
    TreeNode *left;
    TreeNode *right;
    TreeNode(int x) : val(x), left(NULL), right(NULL) {}
};
```

# trick
judge if odd
```cpp
if (x & 1) {}
```
trun a complete binary tree into an array
```cpp
// array index start from 1, node index from 1.
root = A[1]
Left(k) = A[2k]
Right(k) = A[2k+1]
Parent(k) = A[k/2]
```
gcd & lcm after C++17
```cpp
GNU++17 [std=gnu++17]
#include <numeric>
int x = gcd(k, x);
int y = lcm(l,x);
```
