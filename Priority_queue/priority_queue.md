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

