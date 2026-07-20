# 🧵 LeetCode Strings Cheat Sheet (Complete)

> Covers **95%+ of string interview questions** on LeetCode.

---

# Table of Contents

1. String Basics
2. Common Operations
3. Character Operations
4. Frequency Counting
5. HashMap Techniques
6. Two Pointers
7. Sliding Window
8. Prefix/Suffix
9. Palindrome
10. Pattern Matching
11. Stack + Strings
12. String Building
13. Sorting Strings
14. Trie Basics
15. Common Algorithms
16. Time Complexities
17. Common Patterns
18. Interview Tricks
19. Top LeetCode Problems

---

# 1. String Basics

```python
s = "leetcode"
```

Length

```python
len(s)
```

Access

```python
s[0]
s[-1]
```

Slice

```python
s[2:5]
s[:4]
s[4:]
s[::-1]
```

Immutable

```python
s[0] = 'a' ❌
```

Need

```python
lst = list(s)
lst[0] = 'a'
s = "".join(lst)
```

---

# 2. Common Operations

## Concatenate

```python
a + b
```

## Repeat

```python
"a"*5
```

Output

```
aaaaa
```

## Membership

```python
"a" in s
```

## Find

```python
s.find("abc")
```

Returns

```
index
-1 if not found
```

## Index

```python
s.index("abc")
```

Throws exception if absent.

---

## Starts / Ends

```python
s.startswith("ab")
s.endswith("yz")
```

---

## Count

```python
s.count("a")
```

---

## Replace

```python
s.replace("a","b")
```

---

## Split

```python
sentence.split(" ")
```

---

## Join

```python
" ".join(words)
```

---

## Strip

```python
s.strip()
s.lstrip()
s.rstrip()
```

---

## Lower / Upper

```python
s.lower()
s.upper()
```

---

## Capitalize

```python
s.capitalize()
```

---

# 3. Character Operations

ASCII

```python
ord('a')
```

```
97
```

Back

```python
chr(97)
```

Difference

```python
ord(c)-ord('a')
```

Useful for

- frequency arrays
- Caesar cipher
- shifting letters

---

# 4. Frequency Counting

## Counter

```python
from collections import Counter

cnt = Counter(s)
```

Example

```python
cnt['a']
```

---

## Dictionary

```python
freq = {}

for c in s:
    freq[c] = freq.get(c,0)+1
```

---

## Fixed Array

Only lowercase letters

```python
freq = [0]*26

for c in s:
    freq[ord(c)-97]+=1
```

Fastest solution.

---

# 5. HashMap Techniques

Useful for

- Isomorphic Strings
- Word Pattern
- Group Anagrams

Example

```python
seen = {}

for i,c in enumerate(s):
    if c not in seen:
        seen[c]=i
```

---

# 6. Two Pointers

Template

```python
l = 0
r = len(s)-1

while l < r:

    if condition:
        l += 1
    else:
        r -= 1
```

Used for

- Reverse
- Palindrome
- Valid Palindrome
- Reverse Vowels

---

## Reverse

```python
lst = list(s)

l,r = 0,len(lst)-1

while l<r:
    lst[l],lst[r]=lst[r],lst[l]
    l+=1
    r-=1

"".join(lst)
```

---

# 7. Sliding Window ⭐⭐⭐⭐⭐

Most important.

Template

```python
l = 0

for r in range(len(s)):

    # expand

    while invalid:
        l += 1

    ans = max(ans,r-l+1)
```

Problems

- Longest Substring Without Repeating
- Minimum Window
- Permutation in String
- Longest Repeating Character Replacement

---

## No Repeat

```python
seen = set()

l = 0

for r in range(len(s)):

    while s[r] in seen:
        seen.remove(s[l])
        l += 1

    seen.add(s[r])

    ans = max(ans,r-l+1)
```

Complexity

```
O(n)
```

---

# 8. Prefix / Suffix

Prefix

```python
s[:i]
```

Suffix

```python
s[i:]
```

Common problems

- Longest Common Prefix
- Prefix sums
- KMP

---

Longest Common Prefix

```python
prefix = strs[0]

for word in strs:

    while not word.startswith(prefix):
        prefix = prefix[:-1]
```

---

# 9. Palindrome

Check

```python
def isPal(s):

    l,r=0,len(s)-1

    while l<r:

        if s[l]!=s[r]:
            return False

        l+=1
        r-=1

    return True
```

---

Expand Around Center

```python
while l>=0 and r<n and s[l]==s[r]:

    l-=1
    r+=1
```

Used in

- Longest Palindrome

---

# 10. Pattern Matching

## Anagram

```python
Counter(s)==Counter(t)
```

Or

```python
sorted(s)==sorted(t)
```

---

## Isomorphic

```python
map1={}
map2={}
```

Maintain two mappings.

---

## Word Pattern

HashMap both directions.

---

# 11. Stack + Strings

Parentheses

```python
stack=[]

for c in s:

    if opening:
        stack.append(c)

    else:

        if not stack:
            return False

        stack.pop()
```

Problems

- Valid Parentheses
- Remove Stars
- Decode String

---

## Decode String

Pattern

```
3[a2[c]]
```

Need

```
Stack
```

---

# 12. String Builder

Python

Instead of

```python
ans += c
```

Use

```python
res=[]

res.append(c)

return "".join(res)
```

Avoids

```
O(n²)
```

---

# 13. Sorting Strings

Sort characters

```python
"".join(sorted(s))
```

Sort by frequency

```python
Counter(s).most_common()
```

Sort words

```python
sorted(words)
```

Sort custom

```python
sorted(words,key=len)
```

---

# 14. Trie Basics

Node

```python
class TrieNode:

    def __init__(self):
        self.children={}
        self.end=False
```

Insert

```python
node=root

for c in word:

    if c not in node.children:
        node.children[c]=TrieNode()

    node=node.children[c]

node.end=True
```

Problems

- Implement Trie
- Word Search II
- Replace Words

---

# 15. Common Algorithms

## Reverse String

```
Two pointers
```

---

## Reverse Words

```python
" ".join(reversed(sentence.split()))
```

---

## Remove Spaces

```python
"".join(s.split())
```

---

## Remove Duplicates

```python
"".join(dict.fromkeys(s))
```

---

## Caesar Shift

```python
chr((ord(c)-97+k)%26+97)
```

---

## Frequency Sort

```python
Counter(s).most_common()
```

---

## Group Anagrams

```python
key = tuple(sorted(word))
```

Or

```python
freq = [0]*26
```

---

# 16. Time Complexities

| Operation | Complexity |
|-----------|------------|
| len | O(1) |
| indexing | O(1) |
| slicing | O(k) |
| concatenate | O(n) |
| join | O(n) |
| split | O(n) |
| replace | O(n) |
| find | O(n) |
| count | O(n) |
| reverse | O(n) |
| Counter | O(n) |
| sorted | O(n log n) |

---

# 17. Common Patterns

## Pattern 1

Frequency Count

Problems

- Valid Anagram
- Ransom Note

---

## Pattern 2

Two Pointers

Problems

- Reverse String
- Palindrome

---

## Pattern 3

Sliding Window

Problems

- Longest Unique Substring
- Minimum Window

---

## Pattern 4

HashMap

Problems

- Isomorphic
- Word Pattern

---

## Pattern 5

Stack

Problems

- Decode String
- Valid Parentheses

---

## Pattern 6

Trie

Problems

- Prefix Search
- Word Dictionary

---

## Pattern 7

Expand Around Center

Problems

- Longest Palindrome

---

## Pattern 8

Sorting

Problems

- Group Anagrams
- Custom Sort String

---

# 18. Interview Tricks

### Reverse

```python
s[::-1]
```

---

### Check Palindrome

```python
s==s[::-1]
```

---

### Lowercase

```python
s.lower()
```

---

### Digits

```python
c.isdigit()
```

---

### Alphabet

```python
c.isalpha()
```

---

### Alphanumeric

```python
c.isalnum()
```

---

### Space

```python
c.isspace()
```

---

### Uppercase

```python
c.isupper()
```

---

### Lowercase

```python
c.islower()
```

---

# 19. Top String LeetCode Problems

## Easy

- Reverse String
- Valid Anagram
- Valid Palindrome
- First Unique Character
- Ransom Note
- Longest Common Prefix
- Roman to Integer
- Isomorphic Strings
- Reverse Words in a String III
- Detect Capital

---

## Medium

- Longest Substring Without Repeating Characters
- Longest Palindromic Substring
- Group Anagrams
- Decode String
- Partition Labels
- Zigzag Conversion
- String Compression
- Minimum Window Substring
- Find All Anagrams in a String
- Permutation in String
- Remove Duplicate Letters
- Custom Sort String
- Letter Combinations of Phone Number

---

## Hard

- Regular Expression Matching
- Wildcard Matching
- Text Justification
- Minimum Window Substring
- Word Ladder
- Word Search II
- Palindrome Pairs
- Distinct Subsequences
- Edit Distance
- Scramble String

---

# Decision Tree

```
Need frequency?
    ↓
Counter / Array

Need longest/shortest substring?
    ↓
Sliding Window

Need reverse/palindrome?
    ↓
Two Pointers

Need matching pairs?
    ↓
HashMap

Need nested expression?
    ↓
Stack

Need prefix search?
    ↓
Trie

Need rearrangement?
    ↓
Sorting

Need longest palindrome?
    ↓
Expand Around Center

Need pattern search?
    ↓
KMP / Rabin-Karp / Z Algorithm
```

---

# Ultimate Interview Templates

## Frequency

```python
from collections import Counter
cnt = Counter(s)
```

---

## Sliding Window

```python
l = 0

for r in range(len(s)):

    while invalid:
        l += 1

    ans = max(ans,r-l+1)
```

---

## Two Pointers

```python
l,r=0,len(s)-1

while l<r:

    if condition:
        l+=1
    else:
        r-=1
```

---

## HashMap

```python
mp = {}

for i,c in enumerate(s):
    if c not in mp:
        mp[c]=i
```

---

## Stack

```python
stack=[]

for c in s:
    ...
```

---

## Trie

```python
class TrieNode:
    def __init__(self):
        self.children={}
        self.end=False
```

---

## Expand Around Center

```python
def expand(l,r):

    while l>=0 and r<n and s[l]==s[r]:
        l-=1
        r+=1

    return l+1,r-1
```

---

## KMP (LPS Array)

```python
def build_lps(pattern):
    lps = [0] * len(pattern)
    length = 0
    i = 1

    while i < len(pattern):
        if pattern[i] == pattern[length]:
            length += 1
            lps[i] = length
            i += 1
        elif length:
            length = lps[length - 1]
        else:
            lps[i] = 0
            i += 1
    return lps
```

---

## Rabin-Karp (Rolling Hash)

```python
base = 26
mod = 10**9 + 7

hash_val = 0

for c in s:
    hash_val = (hash_val * base + ord(c)) % mod
```

---

## Z-Algorithm

```python
def z_function(s):
    n = len(s)
    z = [0] * n
    l = r = 0

    for i in range(1, n):
        if i <= r:
            z[i] = min(r - i + 1, z[i - l])

        while i + z[i] < n and s[z[i]] == s[i + z[i]]:
            z[i] += 1

        if i + z[i] - 1 > r:
            l, r = i, i + z[i] - 1

    return z
```

---

# Key Takeaway

Most string problems reduce to one of these patterns:

| Pattern | Examples |
|---------|----------|
| Frequency Count | Valid Anagram, Ransom Note |
| Two Pointers | Reverse String, Valid Palindrome |
| Sliding Window | Longest Substring, Minimum Window |
| HashMap | Isomorphic Strings, Word Pattern |
| Stack | Decode String, Valid Parentheses |
| Trie | Word Search II, Replace Words |
| Expand Around Center | Longest Palindromic Substring |
| Sorting | Group Anagrams |
| KMP / Rabin-Karp / Z | Pattern Searching |
