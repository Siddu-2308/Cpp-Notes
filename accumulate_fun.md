# std::accumulate() Cheat Sheet (LeetCode)

## Header

```cpp
#include <numeric>
```

---

# Syntax

```cpp
accumulate(first, last, initial_value);
```

or

```cpp
accumulate(first, last, initial_value, operation);
```

---

# 1. Sum of a Vector

```cpp
vector<int> v = {1,2,3,4,5};

int sum = accumulate(v.begin(), v.end(), 0);

cout << sum; // 15
```

Time: **O(n)**

---

# 2. Sum of Part of a Vector

```cpp
int sum = accumulate(v.begin()+1, v.begin()+4, 0);

// 2 + 3 + 4 = 9
```

---

# 3. Sum with Initial Value

```cpp
int sum = accumulate(v.begin(), v.end(), 100);

// 115
```

Useful when previous answer already exists.

---

# 4. Sum of long long

Very important for LeetCode.

```cpp
vector<int> nums = {1000000000,1000000000};

long long sum = accumulate(nums.begin(), nums.end(), 0LL);
```

**Always use `0LL` when answer may exceed int.**

---

# 5. Product of Elements

```cpp
#include <functional>

int product = accumulate(
    v.begin(),
    v.end(),
    1,
    multiplies<int>()
);
```

Output

```
120
```

---

# 6. Custom Lambda

Sum only even numbers

```cpp
int evenSum = accumulate(
    v.begin(),
    v.end(),
    0,
    [](int sum,int x)
    {
        if(x%2==0)
            return sum+x;
        return sum;
    }
);
```

---

Sum only odd numbers

```cpp
int oddSum = accumulate(
    v.begin(),
    v.end(),
    0,
    [](int sum,int x)
    {
        return x&1 ? sum+x : sum;
    }
);
```

---

# 7. Count Using accumulate

Count even numbers

```cpp
int cnt = accumulate(
    v.begin(),
    v.end(),
    0,
    [](int cnt,int x)
    {
        return cnt+(x%2==0);
    }
);
```

Output

```
Number of even elements
```

---

# 8. Maximum Using accumulate

```cpp
int mx = accumulate(
    v.begin()+1,
    v.end(),
    v[0],
    [](int a,int b)
    {
        return max(a,b);
    }
);
```

Normally use

```cpp
*max_element(v.begin(),v.end());
```

instead.

---

# 9. Minimum Using accumulate

```cpp
int mn = accumulate(
    v.begin()+1,
    v.end(),
    v[0],
    [](int a,int b)
    {
        return min(a,b);
    }
);
```

Normally use

```cpp
*min_element(v.begin(),v.end());
```

---

# 10. XOR of Elements

Useful in Bit Manipulation problems.

```cpp
int xr = accumulate(
    v.begin(),
    v.end(),
    0,
    bit_xor<int>()
);
```

Example

```
1^2^3^2^1 = 3
```

---

# 11. String Concatenation

```cpp
vector<string> words={"I ","Love ","C++"};

string ans = accumulate(
    words.begin(),
    words.end(),
    string("")
);
```

Output

```
I Love C++
```

---

# 12. Build a New String

```cpp
string s="abc";

string ans = accumulate(
    s.begin(),
    s.end(),
    string(""),
    [](string cur,char c)
    {
        return cur+char(toupper(c));
    }
);
```

Output

```
ABC
```

---

# 13. Multiplication Using Lambda

```cpp
int product = accumulate(
    v.begin(),
    v.end(),
    1,
    [](int a,int b)
    {
        return a*b;
    }
);
```

---

# 14. Difference

```cpp
int ans = accumulate(
    v.begin(),
    v.end(),
    0,
    [](int a,int b)
    {
        return a-b;
    }
);
```

Rarely used.

---

# 15. Boolean Result

Are all elements positive?

```cpp
bool ok = accumulate(
    v.begin(),
    v.end(),
    true,
    [](bool cur,int x)
    {
        return cur && (x>0);
    }
);
```

---

# Common LeetCode Examples

## Array Sum

```cpp
int sum = accumulate(nums.begin(), nums.end(), 0);
```

---

## Prefix Sum Initialization

```cpp
int total = accumulate(nums.begin(), nums.end(), 0);
```

---

## Equal Partition

```cpp
int total = accumulate(nums.begin(), nums.end(), 0);

if(total&1)
    return false;
```

---

## Average

```cpp
double avg = (double)accumulate(v.begin(), v.end(), 0)/v.size();
```

---

## Large Sum

```cpp
long long sum = accumulate(v.begin(), v.end(), 0LL);
```

---

## XOR Array

```cpp
int xr = accumulate(
    nums.begin(),
    nums.end(),
    0,
    bit_xor<int>()
);
```

---

# Complexity

| Operation | Time | Space |
|-----------|------|-------|
| Sum | O(n) | O(1) |
| Product | O(n) | O(1) |
| XOR | O(n) | O(1) |
| Lambda | O(n) | O(1) |

---

# Things to Remember

✅ Include

```cpp
#include <numeric>
```

✅ Normal Sum

```cpp
accumulate(v.begin(),v.end(),0);
```

✅ Large Sum

```cpp
accumulate(v.begin(),v.end(),0LL);
```

✅ Product

```cpp
accumulate(v.begin(),v.end(),1,multiplies<int>());
```

✅ XOR

```cpp
accumulate(v.begin(),v.end(),0,bit_xor<int>());
```

✅ Custom

```cpp
accumulate(v.begin(),v.end(),initial,lambda);
```

---

# Interview Tip

For most LeetCode problems, you'll use one of these patterns:

```cpp
// Sum
accumulate(v.begin(), v.end(), 0);

// Large sum
accumulate(v.begin(), v.end(), 0LL);

// Product
accumulate(v.begin(), v.end(), 1, multiplies<int>());

// Custom logic
accumulate(v.begin(), v.end(), init, [](auto a, auto b) {
    // custom operation
});
```
