# C++ Strings Cheat Sheet for LeetCode

> Complete reference for coding interviews and LeetCode.

```cpp
#include <bits/stdc++.h>
using namespace std;
```

---

# 1. Declaration

```cpp
string s;
string s = "hello";
string s("hello");
string s(5, 'a');      // "aaaaa"
```

---

# 2. Input

## Single word

```cpp
cin >> s;
```

Input:
```
hello
```

Output:
```
hello
```

---

## Entire line

```cpp
getline(cin, s);
```

Input:
```
hello world
```

Output:
```
hello world
```

---

# 3. Size

```cpp
s.size();
s.length();   // Same
```

Time: **O(1)**

---

# 4. Check Empty

```cpp
if(s.empty())
```

---

# 5. Access Characters

```cpp
s[0];
s.at(0);

s.front();
s.back();
```

---

# 6. Traverse

## Index

```cpp
for(int i=0;i<s.size();i++)
    cout<<s[i];
```

---

## Range Loop

```cpp
for(char c:s)
    cout<<c;
```

---

## By Reference

```cpp
for(char &c:s)
    c=toupper(c);
```

---

# 7. Append

```cpp
s += 'a';

s += "hello";

s.append("world");

s.push_back('x');
```

---

# 8. Remove Last Character

```cpp
s.pop_back();
```

---

# 9. Insert

```cpp
string s="ace";

s.insert(1,"b");

cout<<s;
```

Output

```
abce
```

---

Insert character

```cpp
s.insert(2,1,'x');
```

Output

```
abxce
```

---

# 10. Erase

```cpp
string s="abcdef";

s.erase(2,3);
```

Removes

```
cde
```

Result

```
abf
```

Erase single character

```cpp
s.erase(s.begin()+2);
```

---

# 11. Replace

```cpp
string s="abcdef";

s.replace(2,3,"XYZ");
```

Result

```
abXYZf
```

---

# 12. Clear

```cpp
s.clear();
```

---

# 13. Swap

```cpp
string a="abc";
string b="xyz";

a.swap(b);
```

---

# 14. Compare

```cpp
if(a==b)

if(a!=b)

if(a>b)
```

Lexicographical comparison.

---

# 15. Substring

```cpp
string s="abcdef";

s.substr(2);
```

Output

```
cdef
```

---

```cpp
s.substr(2,3);
```

Output

```
cde
```

Time

```
O(length)
```

---

# 16. Find

```cpp
string s="leetcode";

s.find("code");
```

Output

```
4
```

Not found

```cpp
if(s.find("abc")==string::npos)
```

---

Find character

```cpp
s.find('e');
```

---

Find after position

```cpp
s.find("abc",5);
```

---

# 17. Reverse Find

```cpp
s.rfind("abc");
```

Searches from end.

---

# 18. Starts With (C++20)

```cpp
s.starts_with("abc");
```

Older compiler

```cpp
s.find("abc")==0
```

---

# 19. Ends With (C++20)

```cpp
s.ends_with("xyz");
```

Older compiler

```cpp
s.substr(s.size()-3)=="xyz";
```

---

# 20. Reverse String

```cpp
reverse(s.begin(),s.end());
```

Time

```
O(n)
```

---

# 21. Sort Characters

```cpp
sort(s.begin(),s.end());
```

Descending

```cpp
sort(s.rbegin(),s.rend());
```

---

# 22. Count Character

```cpp
count(s.begin(),s.end(),'a');
```

---

# 23. Count Frequency

```cpp
vector<int> freq(26);

for(char c:s)
    freq[c-'a']++;
```

---

ASCII

```cpp
unordered_map<char,int> freq;

for(char c:s)
    freq[c]++;
```

---

# 24. Unique Characters

```cpp
sort(s.begin(),s.end());

s.erase(unique(s.begin(),s.end()),s.end());
```

---

# 25. Convert Case

Upper

```cpp
for(char &c:s)
    c=toupper(c);
```

Lower

```cpp
for(char &c:s)
    c=tolower(c);
```

---

# 26. Character Functions

```cpp
isdigit(c)

isalpha(c)

isalnum(c)

islower(c)

isupper(c)

isspace(c)

toupper(c)

tolower(c)
```

---

# 27. String to Integer

```cpp
int x=stoi(s);
```

---

Long long

```cpp
long long x=stoll(s);
```

---

Float

```cpp
float x=stof(s);
```

---

Double

```cpp
double x=stod(s);
```

---

# 28. Number to String

```cpp
string s=to_string(123);
```

---

# 29. Concatenation

```cpp
string a="abc";
string b="def";

string c=a+b;
```

---

# 30. Lexicographical Order

```cpp
apple < banana
```

Dictionary order.

---

# 31. String Iterator

```cpp
for(auto it=s.begin();it!=s.end();it++)
    cout<<*it;
```

Reverse

```cpp
for(auto it=s.rbegin();it!=s.rend();it++)
    cout<<*it;
```

---

# 32. Convert to Char Array

```cpp
char arr[100];

strcpy(arr,s.c_str());
```

---

Pointer

```cpp
const char *p=s.c_str();
```

---

# 33. Split String (stringstream)

```cpp
string s="one two three";

stringstream ss(s);

string word;

while(ss>>word)
    cout<<word<<endl;
```

---

Split by comma

```cpp
string s="a,b,c";

stringstream ss(s);

string token;

while(getline(ss,token,','))
    cout<<token<<endl;
```

---

# 34. Palindrome

```cpp
bool isPalindrome(string s){

    int i=0;
    int j=s.size()-1;

    while(i<j){

        if(s[i]!=s[j])
            return false;

        i++;
        j--;
    }

    return true;
}
```

Time

```
O(n)
```

---

# 35. Reverse Words

```cpp
stringstream ss(s);

vector<string> words;

string word;

while(ss>>word)
    words.push_back(word);

reverse(words.begin(),words.end());
```

---

# 36. Remove Spaces

```cpp
string ans;

for(char c:s)
    if(c!=' ')
        ans+=c;
```

---

# 37. Prefix

```cpp
string prefix=s.substr(0,k);
```

---

# 38. Suffix

```cpp
string suffix=s.substr(s.size()-k);
```

---

# 39. Common STL Algorithms

```cpp
reverse()

sort()

count()

find()

unique()

transform()

rotate()

next_permutation()
```

---

# 40. Transform

Upper

```cpp
transform(s.begin(),s.end(),s.begin(),::toupper);
```

Lower

```cpp
transform(s.begin(),s.end(),s.begin(),::tolower);
```

---

# 41. Rotate

```cpp
rotate(s.begin(),s.begin()+k,s.end());
```

Example

```
abcdef
```

k=2

```
cdefab
```

---

# 42. Next Permutation

```cpp
next_permutation(s.begin(),s.end());
```

Example

```
abc
```

↓

```
acb
```

---

# 43. String Builder

Instead of

```cpp
ans += c;
```

For huge concatenations

```cpp
ostringstream out;

out<<"abc";

out<<123;

string ans=out.str();
```

---

# 44. Common Time Complexities

| Operation | Complexity |
|-----------|------------|
| size() | O(1) |
| empty() | O(1) |
| [] | O(1) |
| push_back() | O(1) amortized |
| pop_back() | O(1) |
| append() | O(n) |
| insert() | O(n) |
| erase() | O(n) |
| replace() | O(n) |
| substr() | O(k) |
| reverse() | O(n) |
| sort() | O(n log n) |
| count() | O(n) |
| find() | O(n) |
| rfind() | O(n) |
| compare() | O(n) |
| clear() | O(n) |

---

# 45. LeetCode Patterns

## Two Pointers

```cpp
int i=0;
int j=s.size()-1;

while(i<j){

    if(s[i]!=s[j]){
        ...
    }

    i++;
    j--;
}
```

---

## Sliding Window

```cpp
int left=0;

for(int right=0;right<s.size();right++){

    while(condition){

        left++;
    }
}
```

---

## Frequency Array

```cpp
vector<int> freq(26);

for(char c:s)
    freq[c-'a']++;
```

---

## Hash Map

```cpp
unordered_map<char,int> mp;

for(char c:s)
    mp[c]++;
```

---

## Build Answer

```cpp
string ans;

for(...)
    ans.push_back(c);
```

---

## Reverse

```cpp
reverse(s.begin(),s.end());
```

---

## Sort

```cpp
sort(s.begin(),s.end());
```

---

## Substring

```cpp
string sub=s.substr(start,len);
```

---

## Find

```cpp
int pos=s.find(pattern);

if(pos!=string::npos){
    ...
}
```

---

# 46. Most Asked String Problems

- Valid Palindrome
- Reverse String
- Reverse Words in a String
- Longest Common Prefix
- Longest Palindromic Substring
- Longest Substring Without Repeating Characters
- Minimum Window Substring
- Group Anagrams
- Valid Anagram
- Find All Anagrams in a String
- String Compression
- Implement strStr()
- Roman to Integer
- Integer to Roman
- Decode String
- Multiply Strings
- Zigzag Conversion
- Compare Version Numbers
- Count and Say
- Text Justification
- Edit Distance
- Wildcard Matching
- Regular Expression Matching
- KMP Pattern Matching
- Rabin-Karp
- Z Algorithm
- Trie-based Word Search

---

# 47. Interview Tips

✅ Prefer `push_back()` for single characters.

✅ Use `substr()` carefully—it creates a new string.

✅ Always compare `find()` against `string::npos`.

✅ Use `unordered_map<char,int>` when character set is unknown.

✅ Use `vector<int>(26)` for lowercase English letters.

✅ Use `reverse()` instead of writing manual reversal unless asked.

✅ Sliding window is the most common pattern for string problems.

✅ Be careful with `getline()` after `cin`; consume the leftover newline with:

```cpp
cin.ignore();
```

---

# Quick Reference

| Task | Function |
|------|----------|
| Length | `s.size()` |
| Empty | `s.empty()` |
| Append | `+=`, `append()` |
| Add char | `push_back()` |
| Remove last | `pop_back()` |
| Insert | `insert()` |
| Delete | `erase()` |
| Replace | `replace()` |
| Substring | `substr()` |
| Find | `find()` |
| Reverse find | `rfind()` |
| Reverse | `reverse()` |
| Sort | `sort()` |
| Count | `count()` |
| Uppercase | `toupper()` / `transform()` |
| Lowercase | `tolower()` / `transform()` |
| String → int | `stoi()` |
| int → String | `to_string()` |
| Split | `stringstream` |
| Reverse | `reverse(begin,end)` |
| Next permutation | `next_permutation()` |
| Rotate | `rotate()` |
| Compare | `==`, `<`, `>` |
| Frequency | `unordered_map` / `vector<int>(26)` |
