# 📌 DSA Sheet – 5: ❓ Alternating Characters  
## 🎯 Problem Level  
**Medium**

---

## 🧩 Background  

You’re given a string that only contains the characters `'A'` and `'B'`.  
Your goal is to **make the string beautiful** by **removing the minimum number of characters**.

A string is **beautiful** if **no two adjacent characters are the same**.

This problem helps build intuition around **string traversal**, **character comparison**, and **greedy deletion** strategy.

---

## 📝 Problem Statement  

Given a string `s`, remove the **minimum number of characters** to ensure **no two adjacent characters are the same**.  

---

## 📥 Input Format  
- A single string `s` containing only `'A'` and `'B'`.

---

## 📤 Output Format  
- An integer — the **minimum number of deletions** required to make the string beautiful.

---

## 🧪 Example  

### 🔹 Testcase 1  
```
Input:  
AAABBB

Output:  
4
```

**Explanation:**  
- Remove two `'A'`s and two `'B'`s: `"AAABBB"` → `"AB"` or `"ABB"` (both valid).  
- In both cases, we removed 4 characters to avoid consecutive duplicates.

---

## ⚙️ Constraints  
- `1 ≤ s.length ≤ 10⁵`  
- Only contains characters `'A'` and `'B'`.

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <string>
using namespace std;

// Function to calculate minimum characters to remove for alternating characters
int minRemoval(string s) {
    int count = 0;
    for (int i = 1; i < s.length(); i++) {
        if (s[i] == s[i - 1]) {
            count++;
        }
    }
    return count;
}

int main() {
    string s;
    cin >> s;
    
    cout << minRemoval(s);
    return 0;
}
```

---

## 🏷️ Tags  
`🧵 Strings` | `🧠 Greedy` | `⚡ Linear Scan`  

---

## 👨‍💻 Author  

### 🚀 **Darshan Vasani**  
💡 **Full-Stack Developer | Software Engineer | Mentor**  

### 🔗 Connect with me! 🌍  
🌐 **Portfolio:** [dpvasani56.vercel.app](https://dpvasani56.vercel.app)  
🐙 **GitHub:** [github.com/dpvasani](https://github.com/dpvasani)  
💼 **LinkedIn:** [linkedin.com/in/dpvasani56](https://www.linkedin.com/in/dpvasani56/)  
🌳 **Linktree:** [linktr.ee/dpvasani56](https://linktr.ee/dpvasani56)  
🎓 **Credly:** [credly.com/users/dpvasani55](https://www.credly.com/users/dpvasani55/)  
🐦 **Twitter:** [x.com/vasanidarshan56](https://x.com/vasanidarshan56)  
📢 **Topmate:** [topmate.io/dpvasani56](https://topmate.io/dpvasani56)

---

🎯 Keep coding – one clean string at a time!  
Coming up: more string manipulation magic in Day 19 🚀