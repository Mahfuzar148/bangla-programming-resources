---

# 🔷 1. Basic `sort()` Syntax

## ✅ Simple sort

```cpp
sort(v.begin(), v.end());
```

👉 এটা default ভাবে:

* ascending order এ sort করে

---

# 🔷 2. Comparator কী?

👉 Comparator হলো এমন একটা function যেটা বলে:

> “কোন element আগে আসবে?”

---

# 🔷 3. General Syntax (Common Form)

## ✅ Full syntax:

```cpp
sort(v.begin(), v.end(), comp);
```

👉 এখানে `comp` = comparator function

---

# 🔷 4. Comparator Function (Normal Function)

## ✅ Example:

```cpp
bool comp(int a, int b) {
    return a > b; // descending
}

sort(v.begin(), v.end(), comp);
```

👉 যদি `true` return করে → `a` আগে আসবে

---

# 🔷 5. Lambda Function (Modern C++)

👉 তুমি যেটা লিখেছো সেটাই lambda

## ✅ General Syntax:

```cpp
sort(v.begin(), v.end(), [](type a, type b) {
    // condition
});
```

---

# 🔷 6. তোমার Code Explanation

```cpp
sort(v.begin(), v.end(), [](pair<int,int> a, pair<int,int> b) {
    if(a.first == b.first)
        return a.second < b.second;
    return a.first > b.first;
});
```

---

## 🧠 কী হচ্ছে এখানে?

👉 Step 1:

* যদি solved same হয় → penalty compare

👉 Step 2:

* penalty ছোট হলে আগে

👉 Step 3:

* না হলে solved বড় আগে

---

# 🔷 7. Beginner Example

## 🔹 Ascending:

```cpp
vector<int> v = {5,2,8,1};

sort(v.begin(), v.end());
```

👉 Output:

```
1 2 5 8
```

---

## 🔹 Descending:

```cpp
sort(v.begin(), v.end(), [](int a, int b){
    return a > b;
});
```

👉 Output:

```
8 5 2 1
```

---

# 🔷 8. Pair Sorting Examples

## 🔹 Default:

```cpp
vector<pair<int,int>> v = {{2,3},{1,5},{2,1}};

sort(v.begin(), v.end());
```

👉 Output:

```
1 5
2 1
2 3
```

---

## 🔹 Custom (like CF ranking):

```cpp
sort(v.begin(), v.end(), [](pair<int,int> a, pair<int,int> b){
    if(a.first == b.first)
        return a.second < b.second;
    return a.first > b.first;
});
```

---

# 🔷 9. Advanced: Struct দিয়ে

```cpp
struct Student {
    int solved, penalty;
};

bool comp(Student a, Student b) {
    if(a.solved == b.solved)
        return a.penalty < b.penalty;
    return a.solved > b.solved;
}
```

---

# 🔷 10. Very Advanced: Multiple Conditions

```cpp
sort(v.begin(), v.end(), [](auto a, auto b){
    if(a.first != b.first)
        return a.first > b.first;
    if(a.second != b.second)
        return a.second < b.second;
    return false;
});
```

---

# 🔷 🔥 Golden Rule (সবচেয়ে গুরুত্বপূর্ণ)

👉 comparator function এ:

```cpp
return TRUE → a আগে
return FALSE → b আগে
```

---

# 🔷 🎯 Shortcut

👉 ascending → `a < b`
👉 descending → `a > b`

---

# 🔷 🚀 Final Summary

| Situation          | Condition |
| ------------------ | --------- |
| ascending          | `a < b`   |
| descending         | `a > b`   |
| multiple condition | `if-else` |

---

