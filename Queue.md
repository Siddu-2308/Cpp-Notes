# Queue Cheat Sheet (C++)

---

# What is a Queue?

FIFO (First In First Out)

```
Front -> [1][2][3][4] <- Rear

Pop : 1
Push: 5

Result:
Front -> [2][3][4][5]
```

---

# STL Queue

```cpp
queue<int> q;
```

## Basic Operations

```cpp
q.push(x);      // Insert at rear
q.pop();        // Remove front
q.front();      // First element
q.back();       // Last element
q.empty();      // true/false
q.size();       // Number of elements
```

Example

```cpp
queue<int> q;

q.push(10);
q.push(20);
q.push(30);

cout << q.front(); //10
cout << q.back();  //30

q.pop();

cout << q.front(); //20
```

---

# Time Complexity

| Operation | Complexity |
|-----------|------------|
| push | O(1) |
| pop | O(1) |
| front | O(1) |
| back | O(1) |
| size | O(1) |
| empty | O(1) |

---

# Queue Traversal

```cpp
while(!q.empty()){
    cout << q.front() << " ";
    q.pop();
}
```

If original queue should remain:

```cpp
queue<int> temp = q;

while(!temp.empty()){
    cout << temp.front() << " ";
    temp.pop();
}
```

---

# Queue using Linked List

```cpp
class Node{
public:
    int val;
    Node* next;

    Node(int x){
        val = x;
        next = nullptr;
    }
};

class Queue{
    Node *front, *rear;

public:

    Queue(){
        front = rear = nullptr;
    }

    void push(int x){

        Node* node = new Node(x);

        if(rear == nullptr){
            front = rear = node;
            return;
        }

        rear->next = node;
        rear = node;
    }

    void pop(){

        if(front == nullptr)
            return;

        Node* temp = front;
        front = front->next;

        if(front == nullptr)
            rear = nullptr;

        delete temp;
    }

    int Front(){

        if(front == nullptr)
            return -1;

        return front->val;
    }

    bool empty(){
        return front == nullptr;
    }
};
```

Complexities

```
Push  : O(1)
Pop   : O(1)
Front : O(1)
```

---

# Circular Queue

Useful when array space should be reused.

Maintain

```cpp
front
rear
size
capacity
```

Insertion

```
rear = (rear + 1) % capacity;
```

Deletion

```
front = (front + 1) % capacity;
```

Conditions

```
Empty -> size == 0

Full -> size == capacity
```

Complexities

```
All operations : O(1)
```

---

# Deque (Double Ended Queue)

```cpp
deque<int> dq;
```

Operations

```cpp
dq.push_front(x);
dq.push_back(x);

dq.pop_front();
dq.pop_back();

dq.front();
dq.back();
```

Complexities

```
All O(1)
```

Useful for

- Sliding Window Maximum
- 0-1 BFS
- Monotonic Queue

---

# Priority Queue (Heap)

Default = Max Heap

```cpp
priority_queue<int> pq;
```

Operations

```cpp
pq.push(x);
pq.pop();
pq.top();
```

Min Heap

```cpp
priority_queue<int, vector<int>, greater<int>> pq;
```

Complexities

| Operation | Complexity |
|-----------|------------|
| push | O(log n) |
| pop | O(log n) |
| top | O(1) |

---

# Monotonic Queue

Maintains increasing/decreasing order.

Template (Decreasing)

```cpp
deque<int> dq;

while(!dq.empty() && dq.back() < x)
    dq.pop_back();

dq.push_back(x);
```

Applications

- Sliding Window Maximum
- DP Optimization

---

# BFS using Queue

```cpp
queue<int> q;

q.push(src);
vis[src] = true;

while(!q.empty()){

    int node = q.front();
    q.pop();

    for(auto child : adj[node]){

        if(!vis[child]){

            vis[child] = true;
            q.push(child);

        }
    }
}
```

Complexity

```
O(V + E)
```

---

# Multi Source BFS

```cpp
queue<pair<int,int>> q;

for(all sources){
    q.push(source);
    vis[source]=1;
}
```

Same BFS afterwards.

---

# Queue vs Stack

| Queue | Stack |
|--------|-------|
| FIFO | LIFO |
| push() | push() |
| pop() removes front | pop() removes top |
| front() | top() |

---

# Common Queue Problems

Easy

- Implement Queue
- Implement Stack using Queues
- Number of Recent Calls
- Design Circular Queue

Medium

- Rotting Oranges
- Open the Lock
- Walls and Gates
- Dota2 Senate
- Time Needed to Buy Tickets
- Reveal Cards in Increasing Order

Hard

- Sliding Window Maximum
- Shortest Subarray with Sum ≥ K
- Trapping Rain Water II
- Bus Routes
- Minimum Cost to Make at Least One Valid Path

---

# Interview Tips

✔ Queue = FIFO

✔ Queue is used in BFS.

✔ Circular Queue avoids wasted array space.

✔ Deque supports insertion/deletion at both ends.

✔ Priority Queue is implemented using Heap.

✔ Sliding Window Maximum → Deque.

✔ BFS → Queue.

✔ Dijkstra → Priority Queue.

✔ 0-1 BFS → Deque.

✔ Normal BFS = Queue

✔ Weighted Graph = Priority Queue

✔ Queue traversal destroys the queue unless copied.
