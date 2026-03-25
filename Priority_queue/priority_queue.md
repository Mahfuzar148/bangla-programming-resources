## 🔷 Priority Queue কী?

**Priority Queue** হলো এক ধরনের ডাটা স্ট্রাকচার যেখানে এলিমেন্টগুলো **priority অনুযায়ী সাজানো থাকে**, সাধারণ queue-এর মতো FIFO (First In First Out) নয়।

### 👉 মূল ধারণা:

* সাধারণ queue → আগে ঢুকলে আগে বের হবে
* priority queue → যার priority বেশি, সে আগে বের হবে

### 👉 C++ এ:

ডিফল্টভাবে `priority_queue` হলো **max heap**
➡️ অর্থাৎ সবচেয়ে বড় মান সবসময় উপরে থাকে (`top()`)

---

## 🔷 Example 1: Basic Priority Queue

### ✅ Code:

```cpp
#include<bits/stdc++.h>
using namespace std;

int main()
{
    priority_queue<int> q;

    q.push(1);
    q.push(2);
    q.push(3);
    q.push(4);

    cout << q.top() << endl; // biggest element
    q.pop();

    cout << q.top() << endl;

    return 0;
}
```

### 🧠 ব্যাখ্যা (বাংলায়):

* `priority_queue<int> q;` → একটি max heap তৈরি করা হলো
* `push()` দিয়ে 1,2,3,4 ঢোকানো হয়েছে
* ভেতরে অর্ডার হবে → **4,3,2,1** (priority অনুযায়ী)

#### 👉 Output:

```
4
3
```

* প্রথম `top()` → 4
* `pop()` করলে 4 বাদ যায়
* এরপর `top()` → 3

---

## 🔷 Example 2: সব এলিমেন্ট প্রিন্ট করা

### ✅ Code:

```cpp
#include<bits/stdc++.h>
using namespace std;

int main()
{
    priority_queue<int> q;

    q.push(1);
    q.push(2);
    q.push(3);
    q.push(4);

    while(!q.empty()) {
        cout << q.top() << endl;
        q.pop();
    }

    cout << q.size() << endl;

    return 0;
}
```

### 🧠 ব্যাখ্যা:

* `while(!q.empty())` → যতক্ষণ queue খালি না হয়
* প্রতিবার:

  * `top()` → সবচেয়ে বড় মান নেয়
  * `pop()` → সেটাকে সরিয়ে দেয়

#### 👉 Output:

```
4
3
2
1
0
```

* শেষে `size()` → 0 (সব pop হয়ে গেছে)

---

## 🔷 Example 3: Duplicate values সহ

### ✅ Code:

```cpp
#include<bits/stdc++.h>
using namespace std;

int main()
{
    priority_queue<int> q;

    q.push(1);
    q.push(2);
    q.push(2);
    q.push(3);
    q.push(4);

    while(!q.empty()) {
        cout << q.top() << endl;
        q.pop();
    }

    cout << q.size() << endl;

    return 0;
}
```

### 🧠 ব্যাখ্যা:

* এখানে 2 দুইবার আছে
* priority queue duplicate value সাপোর্ট করে

#### 👉 Output:

```
4
3
2
2
1
0
```

---

## 🔷 Example 4: Min Heap (ছোটটা আগে বের হবে)

### ✅ Code:

```cpp
#include<bits/stdc++.h>
using namespace std;

int main()
{
    priority_queue<int, vector<int>, greater<int>> q;

    q.push(1);
    q.push(2);
    q.push(2);
    q.push(3);
    q.push(4);

    while(!q.empty()) {
        cout << q.top() << endl;
        q.pop();
    }

    cout << q.size() << endl;

    return 0;
}
```

### 🧠 ব্যাখ্যা:

* `greater<int>` ব্যবহার করলে **min heap** হয়
* অর্থাৎ সবচেয়ে ছোট মান আগে আসবে

#### 👉 Output:

```
1
2
2
3
4
0
```

---

## 🔷 সারাংশ

| টাইপ                            | আচরণ               |
| ------------------------------- | ------------------ |
| Default (`priority_queue<int>`) | Max Heap (বড় আগে)  |
| `greater<int>`                  | Min Heap (ছোট আগে) |

---



---

# 🔷 1. Min Heap with Pair (ascending order)

## ✅ Code:

```cpp
#include<bits/stdc++.h>
using namespace std;

int main()
{
    priority_queue<pair<int,int>, vector<pair<int,int>>, greater<pair<int,int>>> q;

    q.push({1, 2});
    q.push({2, 3});
    q.push({2, 4});
    q.push({4, 4});
    q.push({3, 4});

    while(!q.empty()) {
        cout << q.top().first << " " << q.top().second << endl;
        q.pop();
    }

    cout << q.size() << endl;

    return 0;
}
```

---

## 🧠 ব্যাখ্যা (বাংলায়):

### 👉 1. এই লাইনের মানে:

```cpp
priority_queue<pair<int,int>, vector<pair<int,int>>, greater<pair<int,int>>> q;
```

* `pair<int,int>` → দুইটা মান (first, second)
* `greater<>` → **min heap** (ছোট আগে আসবে)

---

### 👉 2. push করা:

```cpp
q.push({1, 2});
q.push({2, 3});
q.push({2, 4});
q.push({4, 4});
q.push({3, 4});
```

👉 pair গুলো compare হবে এভাবে:

1. আগে `first`
2. যদি equal হয় → `second`

---

### 👉 3. Sorting order:

```
(1,2)
(2,3)
(2,4)
(3,4)
(4,4)
```

---

### 👉 4. Output:

```
1 2
2 3
2 4
3 4
4 4
0
```

---

# 🔷 2. Default Priority Queue (Max Heap)

## ✅ Code:

```cpp
#include<bits/stdc++.h>
using namespace std;

int main()
{
    priority_queue<pair<int,int>> q;

    q.push({1, 2});
    q.push({2, 3});
    q.push({2, 4});
    q.push({4, 4});
    q.push({3, 4});

    while(!q.empty()) {
        cout << q.top().first << " " << q.top().second << endl;
        q.pop();
    }

    cout << q.size() << endl;

    return 0;
}
```

---

## 🧠 ব্যাখ্যা:

👉 এখানে `greater<>` নেই
➡️ তাই এটা **max heap**

---

### 👉 Sorting order:

```
(4,4)
(3,4)
(2,4)
(2,3)
(1,2)
```

---

### 👉 Output:

```
4 4
3 4
2 4
2 3
1 2
0
```

---

# 🔷 🔥 Important Concept (খুব জরুরি)

## 👉 pair compare rule:

```
(a,b) < (c,d)
```

➡️ যদি:

* a < c → ছোট
* a == c → b < d

---

# 🔷 🎯 Shortcut

| Type     | Code                            | Behavior |
| -------- | ------------------------------- | -------- |
| Max Heap | `priority_queue<pair<int,int>>` | বড় আগে   |
| Min Heap | `greater<pair<int,int>>`        | ছোট আগে  |

---

# 🔷 💡 Real Life Use

👉 এই ধরনের pair priority queue ব্যবহার হয়:

* Dijkstra Algorithm
* Graph problems
* Scheduling

---


---

# 🔷 🧩 Problem: **Contest Ranking**

## 📄 Problem Statement

একটি প্রোগ্রামিং কনটেস্টে `n` জন প্রতিযোগী অংশগ্রহণ করেছে।

প্রতিটি প্রতিযোগীর জন্য দুটি তথ্য দেওয়া আছে:

* `solved` → সে কতটি সমস্যা সমাধান করেছে
* `penalty` → তার মোট penalty (সময়)

তোমার কাজ হলো প্রতিযোগীদের এমনভাবে সাজানো (ranking করা):

---

## 🏆 Ranking Rules:

1. যে **বেশি সমস্যা solve করেছে**, সে আগে থাকবে
2. যদি solve সংখ্যা সমান হয়, তাহলে যার **penalty কম**, সে আগে থাকবে

---

## 📥 Input

* প্রথম লাইনে একটি সংখ্যা `n`
* পরবর্তী `n` লাইনে দুটি সংখ্যা:

  * `solved`
  * `penalty`

---

## 📤 Output

* প্রতিটি লাইনে sorted order অনুযায়ী `solved penalty` print করো

---

## 📌 Example

### Input:

```
5
1 2
2 3
2 4
4 4
3 4
```

### Output:

```
4 4
3 4
2 3
2 4
1 2
```

---

# 🔷 💡 Solution Idea

👉 আমাদের rule:

* solved → বেশি আগে (descending)
* penalty → কম আগে (ascending)

👉 কিন্তু `priority_queue` default:

* বড় আগে আনে (max heap)

👉 তাই trick:

* penalty কে negative করে push করি

---

# 🔷 ✅ Code (Priority Queue Trick)

```cpp
#include<bits/stdc++.h>
using namespace std;

int main()
{
    int n;
    cin >> n;

    priority_queue<pair<int,int>> q;

    for(int i = 0; i < n; i++) {
        int solved, penalty;
        cin >> solved >> penalty;

        q.push({solved, -penalty}); // trick
    }

    while(!q.empty()) {
        cout << q.top().first << " " << -q.top().second << endl;
        q.pop();
    }

    return 0;
}
```

---

# 🔷 🧠 Explanation (বাংলায়)

### 👉 কেন `-penalty`?

* আমরা চাই penalty কম হলে আগে আসুক
* কিন্তু max heap বড় মান আগে নেয়
* তাই penalty কে negative করি

✔ ফলে:

* ছোট penalty → বড় negative → আগে আসে

---

# 🔷 🔥 Alternative Solution (Best & Clean)

👉 comparator দিয়ে solve করা (recommended)

```cpp
#include<bits/stdc++.h>
using namespace std;

int main()
{
    int n;
    cin >> n;

    vector<pair<int,int>> v;

    for(int i = 0; i < n; i++) {
        int solved, penalty;
        cin >> solved >> penalty;
        v.push_back({solved, penalty});
    }

    sort(v.begin(), v.end(), [](pair<int,int> a, pair<int,int> b) {
        if(a.first == b.first)
            return a.second < b.second; // কম penalty আগে
        return a.first > b.first; // বেশি solved আগে
    });

    for(auto p : v) {
        cout << p.first << " " << p.second << endl;
    }

    return 0;
}
```

---

# 🔷 🎯 Key Takeaway

👉 Codeforces ranking logic:

* **More solved → higher rank**
* **Same solved → lower penalty → higher rank**

---
