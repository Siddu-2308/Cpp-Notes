# C++ Vector Cheat Sheet (LeetCode)

## 1. Declaration

```cpp
vector<int> v;
vector<int> v(5);
vector<int> v(5, 10);

vector<vector<int>> mat;
vector<vector<int>> mat(3, vector<int>(4, 0));
```

---

## 2. Initialization

```cpp
vector<int> v = {1,2,3,4};

vector<vector<int>> mat = {
    {1,2},
    {3,4}
};
```

---

## 3. Size

```cpp
v.size();
v.empty();
```

---

## 4. Access

```cpp
v[0];
v.at(0);
v.front();
v.back();
```

---

## 5. Add Elements

```cpp
v.push_back(10);
v.emplace_back(20);
```

---

## 6. Remove Elements

```cpp
v.pop_back();
```

---

## 7. Insert

```cpp
v.insert(v.begin() + 2, 100);

v.insert(v.begin(), 3, 5);

vector<int> a = {1,2};
vector<int> b = {3,4};

a.insert(a.end(), b.begin(), b.end());
```

---

## 8. Erase

```cpp
v.erase(v.begin() + 2);

v.erase(v.begin() + 1, v.begin() + 4);
```

---

## 9. Clear

```cpp
v.clear();
```

---

## 10. Resize

```cpp
v.resize(10);
v.resize(10, 7);
```

---

## 11. Assign

```cpp
v.assign(5, 100);
```

---

## 12. Swap

```cpp
a.swap(b);
```

---

## 13. Copy / Reference

```cpp
vector<int> copy = v;

vector<int>& ref = v;

const vector<int>& cref = v;
```

---

## 14. Traversing

### Index Loop

```cpp
for(int i = 0; i < v.size(); i++)
    cout << v[i];
```

### Range Loop

```cpp
for(int x : v)
    cout << x;
```

Modify

```cpp
for(int &x : v)
    x++;
```

### Iterator

```cpp
for(auto it = v.begin(); it != v.end(); it++)
    cout << *it;
```

Reverse

```cpp
for(auto it = v.rbegin(); it != v.rend(); it++)
    cout << *it;
```

---

## 15. Sort

Ascending

```cpp
sort(v.begin(), v.end());
```

Descending

```cpp
sort(v.begin(), v.end(), greater<int>());
```

---

## 16. Reverse

```cpp
reverse(v.begin(), v.end());
```

---

## 17. Maximum & Minimum

```cpp
*max_element(v.begin(), v.end());

*min_element(v.begin(), v.end());
```

---

## 18. Sum

```cpp
#include <numeric>

int sum = accumulate(v.begin(), v.end(), 0);
```

---

## 19. Count

```cpp
count(v.begin(), v.end(), 5);
```

---

## 20. Find

```cpp
auto it = find(v.begin(), v.end(), 5);

if(it != v.end())
{
    int index = it - v.begin();
}
```

---

## 21. Binary Search

```cpp
binary_search(v.begin(), v.end(), 10);
```

**Vector must be sorted.**

---

## 22. Lower Bound

```cpp
auto it = lower_bound(v.begin(), v.end(), 5);

int index = it - v.begin();
```

Returns first element **>= x**

---

## 23. Upper Bound

```cpp
auto it = upper_bound(v.begin(), v.end(), 5);
```

Returns first element **> x**

---

## 24. Remove Duplicates

```cpp
sort(v.begin(), v.end());

v.erase(unique(v.begin(), v.end()), v.end());
```

---

## 25. Rotate

```cpp
rotate(v.begin(), v.begin() + 2, v.end());
```

Example:

```
1 2 3 4 5

↓

3 4 5 1 2
```

---

## 26. Fill

```cpp
fill(v.begin(), v.end(), 0);
```

---

## 27. Compare

```cpp
if(a == b)
{
    cout << "Equal";
}
```

---

## 28. 2D Vector

```cpp
vector<vector<int>> mat(3, vector<int>(4, 0));

mat[i][j];

mat.push_back({1,2,3});
```

---

## 29. Vector of Pairs

```cpp
vector<pair<int,int>> vp;

vp.push_back({1,2});

vp.emplace_back(3,4);

for(auto p : vp)
{
    cout << p.first << " " << p.second;
}
```

---

## 30. Vector of Strings

```cpp
vector<string> words;

words.push_back("hello");
```

---

## 31. Useful STL Algorithms

```cpp
sort(v.begin(), v.end());

reverse(v.begin(), v.end());

find(v.begin(), v.end(), x);

count(v.begin(), v.end(), x);

max_element(v.begin(), v.end());

min_element(v.begin(), v.end());

accumulate(v.begin(), v.end(), 0);

binary_search(v.begin(), v.end(), x);

lower_bound(v.begin(), v.end(), x);

upper_bound(v.begin(), v.end(), x);

next_permutation(v.begin(), v.end());

prev_permutation(v.begin(), v.end());

rotate(v.begin(), v.begin()+k, v.end());

fill(v.begin(), v.end(), value);

unique(v.begin(), v.end());
```

---

## 32. Passing Vector to Functions

Copy

```cpp
void solve(vector<int> v)
```

Reference (Preferred)

```cpp
void solve(vector<int>& v)
```

Read-only Reference

```cpp
void solve(const vector<int>& v)
```

---

## 33. Nested Traversal

```cpp
for(auto &row : mat)
{
    for(auto x : row)
        cout << x << " ";

    cout << endl;
}
```

---

# Headers

```cpp
#include <bits/stdc++.h>
using namespace std;
```

---

# Most Important Functions for LeetCode

- push_back()
- pop_back()
- size()
- empty()
- clear()
- sort()
- reverse()
- find()
- count()
- max_element()
- min_element()
- accumulate()
- binary_search()
- lower_bound()
- upper_bound()
- insert()
- erase()
- resize()
- assign()
- swap()
- fill()
- unique()
- rotate()

Master these and you'll handle almost every vector-based LeetCode problem.
