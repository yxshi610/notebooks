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
## binary
```cpp
// [l,mid] + [mid+1,r]
while (l < r) {
  int mid = l + r >> 1;
  if (satisfy(mid)) r = mid;
  else {l = mid + 1;}
}
return l;

// [l,mid-1] + [mid,r]
while (l < r) {
  int mid = l + r + 1 >> 1;
  if (satisfy(mid)) l = mid;
  else {r = mid-1;}
}
return l;
```


## quick sort
pivot->sort->recursion
```cpp
void quick_sort(int a[], int l, int r) {
    if (l >= r) return;
    int p = a[(l+r)/2], i = l-1, j = r+1;
    while (i<j) {
        do i++; while (a[i] < p);
        do j--; while (a[j] > p);
        if (i<j) swap(a[i], a[j]);
    }
    quick_sort(a,l,j);
    quick_sort(a,j+1,r);
}
```
## merge sort
recursion->sort
```cpp
void merge_sort(int a[], int l, int r) {
    if (l >= r) return;
    int mid = l + r >> 1;
    merge_sort(a, l, mid);
    merge_sort(a, mid+1, r);
    int k=0, i = l, j = mid+1;
    while (i <= mid && j <= r) {
        if (a[i] <= a[j]) tmp[k++] = a[i++];
        else {tmp[k++] = a[j++];}
    }
    while (i <= mid) tmp[k++] = a[i++];
    while (j <= r) tmp[k++] = a[j++];
    for (int i = l, j = 0; i <= r; ++i, ++j) a[i] = tmp[j];
}
```

## Next Greater Element
```cpp
vector<int> NextGreaterElement(vector<int> nums) {
    int n = nums.size();
    vector<int> res(n);
    stack<int> s;
    for (int i = n - 1; i >= 0; i--) {
        while (!s.empty() && s.top() <= nums[i]) {
            s.pop();
        }
        res[i] = s.empty() ? n : s.top();
        s.push(nums[i]);
    }
    return res;
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

```cpp
// get permutation with STL
vector<vector<int>> permutation(vector<int>& nums) {
    sort(nums.begin(), nums.end());
    vector<vector<int>> res;
    do res.emplace_back(nums);
    while (next_permutation(nums.begin(), nums.end()));
    return res;
}
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
