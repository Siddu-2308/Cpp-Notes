# Linked List Cheat Sheet (C++)

> Covers 95%+ of Linked List problems on LeetCode.

---

# Definition

```cpp
struct ListNode {
    int val;
    ListNode *next;

    ListNode() : val(0), next(nullptr) {}
    ListNode(int x) : val(x), next(nullptr) {}
    ListNode(int x, ListNode *next) : val(x), next(next) {}
};
```

---

# Traversing

```cpp
ListNode* curr = head;

while (curr) {
    cout << curr->val << " ";
    curr = curr->next;
}
```

Time: O(n)

---

# Create New Node

```cpp
ListNode* node = new ListNode(5);
```

---

# Insert at Beginning

```cpp
ListNode* node = new ListNode(val);
node->next = head;
head = node;
```

---

# Insert After Current Node

```cpp
ListNode* node = new ListNode(val);

node->next = curr->next;
curr->next = node;
```

---

# Delete Next Node

```cpp
ListNode* temp = curr->next;
curr->next = temp->next;
delete temp;
```

---

# Delete Head

```cpp
ListNode* temp = head;
head = head->next;
delete temp;
```

---

# Find Length

```cpp
int len = 0;

ListNode* curr = head;

while(curr){
    len++;
    curr = curr->next;
}
```

---

# Reverse Linked List (Most Important)

```cpp
ListNode* prev = nullptr;
ListNode* curr = head;

while(curr){

    ListNode* next = curr->next;

    curr->next = prev;

    prev = curr;
    curr = next;
}

return prev;
```

Time: O(n)

Used in:

- Reverse Linked List
- Palindrome
- Reorder List
- Reverse K Group
- Reverse II

---

# Reverse Recursive

```cpp
ListNode* reverse(ListNode* head){

    if(head==nullptr || head->next==nullptr)
        return head;

    ListNode* newHead = reverse(head->next);

    head->next->next = head;
    head->next = nullptr;

    return newHead;
}
```

---

# Fast Slow Pointer

```cpp
ListNode* slow = head;
ListNode* fast = head;

while(fast && fast->next){

    slow = slow->next;
    fast = fast->next->next;
}
```

Applications:

- Middle node
- Cycle detection
- Palindrome
- Reorder List
- Split List

---

# Find Middle

Second middle:

```cpp
slow=head;
fast=head;

while(fast && fast->next){

    slow=slow->next;
    fast=fast->next->next;
}

return slow;
```

First middle:

```cpp
slow=head;
fast=head->next;

while(fast && fast->next){

    slow=slow->next;
    fast=fast->next->next;
}
```

---

# Detect Cycle (Floyd)

```cpp
ListNode* slow=head;
ListNode* fast=head;

while(fast && fast->next){

    slow=slow->next;
    fast=fast->next->next;

    if(slow==fast)
        return true;
}

return false;
```

LC 141

---

# Find Start of Cycle

```cpp
ListNode* slow=head;
ListNode* fast=head;

while(fast && fast->next){

    slow=slow->next;
    fast=fast->next->next;

    if(slow==fast){

        slow=head;

        while(slow!=fast){

            slow=slow->next;
            fast=fast->next;
        }

        return slow;
    }
}

return nullptr;
```

LC 142

---

# Merge Two Sorted Lists

```cpp
ListNode dummy;

ListNode* tail=&dummy;

while(l1 && l2){

    if(l1->val < l2->val){

        tail->next=l1;
        l1=l1->next;

    }else{

        tail->next=l2;
        l2=l2->next;
    }

    tail=tail->next;
}

tail->next = l1 ? l1 : l2;

return dummy.next;
```

LC 21

---

# Dummy Node Pattern (Very Important)

```cpp
ListNode dummy(0);

dummy.next=head;

ListNode* prev=&dummy;
```

Useful for

- Remove Nth Node
- Swap Pairs
- Reverse II
- Delete Duplicates
- Partition List

---

# Remove Nth Node From End

```cpp
ListNode dummy(0);
dummy.next=head;

ListNode* fast=&dummy;
ListNode* slow=&dummy;

for(int i=0;i<=n;i++)
    fast=fast->next;

while(fast){

    fast=fast->next;
    slow=slow->next;
}

slow->next=slow->next->next;

return dummy.next;
```

LC 19

---

# Merge Point of Two Lists

```cpp
ListNode* a=headA;
ListNode* b=headB;

while(a!=b){

    a = a ? a->next : headB;
    b = b ? b->next : headA;
}

return a;
```

LC 160

---

# Remove Elements

```cpp
ListNode dummy(0);

dummy.next=head;

ListNode* curr=&dummy;

while(curr->next){

    if(curr->next->val==val){

        curr->next=curr->next->next;

    }else{

        curr=curr->next;
    }
}

return dummy.next;
```

LC 203

---

# Delete Duplicates (Sorted)

```cpp
ListNode* curr=head;

while(curr && curr->next){

    if(curr->val==curr->next->val)

        curr->next=curr->next->next;

    else

        curr=curr->next;
}
```

LC 83

---

# Palindrome Linked List

Steps

1. Find middle
2. Reverse second half
3. Compare

```cpp
slow=head;
fast=head;

while(fast && fast->next){

    slow=slow->next;
    fast=fast->next->next;
}

ListNode* second=reverse(slow);

while(second){

    if(head->val!=second->val)
        return false;

    head=head->next;
    second=second->next;
}

return true;
```

LC 234

---

# Reorder List

Pattern

```
Find Middle

↓

Reverse Second Half

↓

Merge Alternately
```

LC 143

---

# Odd Even List

```cpp
odd=head;

even=head->next;

evenHead=even;

while(even && even->next){

    odd->next=even->next;
    odd=odd->next;

    even->next=odd->next;
    even=even->next;
}

odd->next=evenHead;
```

LC 328

---

# Partition List

Dummy nodes

```cpp
ListNode beforeDummy(0);
ListNode afterDummy(0);

ListNode* before=&beforeDummy;
ListNode* after=&afterDummy;

while(head){

    if(head->val<x){

        before->next=head;
        before=before->next;

    }else{

        after->next=head;
        after=after->next;
    }

    head=head->next;
}

after->next=nullptr;

before->next=afterDummy.next;

return beforeDummy.next;
```

LC 86

---

# Swap Nodes in Pairs

Pattern

```
Dummy

↓

prev

↓

first

↓

second
```

LC 24

---

# Reverse K Group

Pattern

```
Dummy

↓

Find kth

↓

Reverse

↓

Reconnect
```

LC 25

---

# Merge K Lists

Techniques

- Min Heap
- Divide & Conquer

Time

Heap → O(N log K)

---

# Copy Random Pointer

Technique

HashMap

```
Old Node

↓

New Node
```

LC 138

---

# Rotate List

Length

↓

k %= length

↓

Find new tail

↓

Break

↓

Reconnect

LC 61

---

# Pointer Tricks

Current

```cpp
curr = curr->next;
```

Next

```cpp
curr->next
```

Skip Node

```cpp
curr->next = curr->next->next;
```

Save Next

```cpp
ListNode* next = curr->next;
```

---

# Dummy Node Template

```cpp
ListNode dummy(0);

dummy.next=head;

ListNode* prev=&dummy;

while(prev->next){

}
```

---

# Reverse Template

```cpp
prev=nullptr;

curr=head;

while(curr){

    next=curr->next;

    curr->next=prev;

    prev=curr;

    curr=next;
}
```

---

# Fast Slow Template

```cpp
slow=head;
fast=head;

while(fast && fast->next){

    slow=slow->next;

    fast=fast->next->next;
}
```

---

# Merge Template

```cpp
dummy

tail

while(a && b)

attach smaller

tail->next = remaining
```

---

# Common Patterns

| Pattern | Used In |
|----------|----------|
| Dummy Node | Delete, Insert, Swap |
| Fast & Slow | Middle, Cycle, Palindrome |
| Reverse | Reverse List, Reorder |
| Two Pointer | Remove Nth, Merge |
| HashMap | Copy Random Pointer |
| Recursion | Reverse, Merge |
| Divide & Conquer | Merge K Lists |
| Heap | Merge K Lists |

---

# Complexity Cheat Sheet

| Operation | Time | Space |
|------------|------|-------|
| Traverse | O(n) | O(1) |
| Reverse | O(n) | O(1) |
| Find Middle | O(n) | O(1) |
| Detect Cycle | O(n) | O(1) |
| Merge Lists | O(n) | O(1) |
| Remove Nth | O(n) | O(1) |
| Reverse K | O(n) | O(1) |
| Merge K (Heap) | O(N log K) | O(K) |

---

# Most Asked LeetCode Problems

- ✅ 21 Merge Two Sorted Lists
- ✅ 19 Remove Nth Node From End
- ✅ 24 Swap Nodes in Pairs
- ✅ 25 Reverse Nodes in K Group
- ✅ 61 Rotate List
- ✅ 83 Remove Duplicates
- ✅ 86 Partition List
- ✅ 92 Reverse Linked List II
- ✅ 141 Linked List Cycle
- ✅ 142 Linked List Cycle II
- ✅ 143 Reorder List
- ✅ 160 Intersection of Two Lists
- ✅ 203 Remove Linked List Elements
- ✅ 206 Reverse Linked List
- ✅ 234 Palindrome Linked List
- ✅ 328 Odd Even Linked List
- ✅ 138 Copy List with Random Pointer
- ✅ 23 Merge K Sorted Lists

---

# Golden Rule

Whenever solving a Linked List problem, first ask:

1. Do I need a **Dummy Node**?
2. Do I need **Fast & Slow pointers**?
3. Do I need to **Reverse** a list?
4. Do I need **Two Pointers**?
5. Do I need a **HashMap**?
6. Am I reconnecting nodes correctly?
7. Did I handle `nullptr` cases?
