# Stack - Ultimate Cheat Sheet (C++)

## What is a Stack?
- **LIFO** (Last In First Out)
- Insertion & deletion happen only at the **Top**

```
Push:    1 2 3
Top ->   3

Pop:
Removes 3
```

---

# STL Stack

```cpp
#include <stack>
using namespace std;

stack<int> st;
```

---

# Basic Operations

### Push

```cpp
st.push(10);
```

### Pop

```cpp
st.pop();          // Removes top
```

### Top

```cpp
cout << st.top();
```

### Empty

```cpp
if(st.empty())
```

### Size

```cpp
st.size();
```

---

# Time Complexity

| Operation | Complexity |
|------------|------------|
| push | O(1) |
| pop | O(1) |
| top | O(1) |
| empty | O(1) |
| size | O(1) |

---

# Traverse Stack

Since stack has no iterators.

```cpp
while(!st.empty()){
    cout << st.top() << " ";
    st.pop();
}
```

Need original?

```cpp
stack<int> temp = st;
```

---

# Reverse Stack

Using recursion

```cpp
insertBottom()

reverse()
```

Time: **O(n²)**

Using another stack

```cpp
stack<int> s2;
```

Time: **O(n)**

---

# Implement Stack

## 1. Array

```cpp
int arr[n];
int top = -1;
```

Push

```cpp
arr[++top] = x;
```

Pop

```cpp
top--;
```

Top

```cpp
arr[top];
```

Overflow

```cpp
top == n-1
```

Underflow

```cpp
top == -1
```

All operations → **O(1)**

---

## 2. Linked List

```cpp
Node* top = nullptr;
```

Push

Insert at head

Pop

Delete head

Top

```cpp
top->data
```

Operations → **O(1)**

No overflow (except memory)

---

# Monotonic Stack

Maintains elements in sorted order.

## Increasing Stack

```cpp
while(!st.empty() && st.top() > x)
    st.pop();

st.push(x);
```

## Decreasing Stack

```cpp
while(!st.empty() && st.top() < x)
    st.pop();

st.push(x);
```

Applications

- Next Greater Element
- Next Smaller Element
- Histogram
- Rain Water
- Stock Span

---

# Expression Problems

## Balanced Parentheses

Push opening brackets.

On closing

- Check top
- Match pair
- Pop

Finally

```cpp
st.empty()
```

---

## Infix → Postfix

Priority

```
^ : 3
* / : 2
+ - : 1
```

Rules

- Operand → Output
- '(' → Push
- ')' → Pop until '('
- Operator
  - Pop while higher/equal precedence
  - Push current

---

## Postfix Evaluation

Operand

```cpp
push(number)
```

Operator

```cpp
b = st.top(); st.pop();
a = st.top(); st.pop();

push(a op b);
```

---

# Famous Problems

- Valid Parentheses
- Min Stack
- Daily Temperatures
- Next Greater Element
- Largest Rectangle in Histogram
- Trapping Rain Water
- Asteroid Collision
- Decode String
- Remove K Digits
- Simplify Path
- Evaluate Reverse Polish Notation
- Stock Span
- Online Stock Span

---

# Stack + Recursion

Function calls use a stack.

Stores

- Local variables
- Parameters
- Return address

Deep recursion

```
Stack Overflow
```

---

# DFS using Stack

```cpp
stack<int> st;

st.push(src);

while(!st.empty()){
    int node = st.top();
    st.pop();

    for(auto x: adj[node])
        st.push(x);
}
```

---

# Two Stacks in One Array

```
top1 -> left

<- free space ->

right <- top2
```

Condition

```cpp
top1 + 1 == top2
```

---

# Min Stack

Maintain

```
stack<int> st;
stack<int> mn;
```

Push

```cpp
if(mn.empty() || x <= mn.top())
    mn.push(x);

st.push(x);
```

Pop

```cpp
if(st.top() == mn.top())
    mn.pop();

st.pop();
```

Minimum

```cpp
mn.top();
```

All operations → **O(1)**

---

# Common Interview Patterns

### Next Greater

```cpp
while(!st.empty() && st.top() <= x)
    st.pop();
```

---

### Previous Greater

Traverse left → right.

---

### Next Smaller

```cpp
while(!st.empty() && st.top() >= x)
    st.pop();
```

---

### Previous Smaller

Traverse left → right.

---

# Common Mistakes

❌ Calling `top()` on empty stack

❌ Forgetting `pop()`

❌ Wrong operand order in postfix evaluation

```cpp
a op b
```

NOT

```cpp
b op a
```

❌ Mixing increasing/decreasing monotonic stacks

❌ Popping before saving `top()`

---

# Complexity Summary

| Operation | Complexity |
|------------|------------|
| Push | O(1) |
| Pop | O(1) |
| Top | O(1) |
| Empty | O(1) |
| Size | O(1) |
| Traverse | O(n) |
| Reverse (extra stack) | O(n) |
| Reverse (recursion) | O(n²) |
| Monotonic Stack | O(n) amortized |

---

# STL Summary

```cpp
stack<int> st;

st.push(x);

st.pop();

st.top();

st.empty();

st.size();
```

---

# Recognition Guide

| Problem Says | Think |
|--------------|-------|
| Undo | Stack |
| Balanced brackets | Stack |
| Nearest greater/smaller | Monotonic Stack |
| Histogram | Monotonic Stack |
| DFS iterative | Stack |
| Expression evaluation | Stack |
| Function calls | Call Stack |
| Reverse data | Stack |
