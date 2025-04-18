# 📌 DSA Sheet – 3 : ❓ Longest Balanced Substring  
## 🎯 Problem Level  
**Medium** — Y (With Hint)

---

## 🧩 Background  

You are analyzing a string that consists **only of `'('` and `')'` characters**.  
Your goal is to **find the length of the longest well-balanced substring**.

A substring is said to be **well-balanced** if:  
1. It contains an **equal number** of opening `'('` and closing `')'` brackets.  
2. Every closing bracket `')'` must have a **corresponding unmatched opening `'('`** before it.

🧠 This problem appears in **parsing engines**, **expression evaluations**, and **editor compilers** to validate **balanced parentheses**.

---

## 📝 Problem Statement  

Given a string `s` consisting of only `'('` and `')'`, return the **length of the longest valid (well-balanced) substring**.

---

## 📥 Input Format  
- A single string `s` made up of `'('` and `')'` characters.

---

## 📤 Output Format  
- Return a single integer: the **length** of the longest well-balanced substring.

---

## 🧪 Example  

### 🔹 Testcase 1  
```
Input:  
(()  

Output:  
2
```

**Explanation:**  
- The substring `"()"` is a valid well-balanced substring with length `2`.  
- The full string `"(()"` is **not balanced** because there's one unmatched `'('`.

---

## ⚙️ Constraints  
- `1 ≤ s.length ≤ 10⁵`  
- String contains only `'('` and `')'`

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <string>
#include <stack>
using namespace std;

// Function to find the longest well-balanced substring
int longestBalancedSubstring(string s) {
    stack<int> st;
    st.push(-1); // base for valid substring
    int maxLen = 0;

    for (int i = 0; i < s.size(); ++i) {
        if (s[i] == '(') {
            st.push(i); // track index of '('
        } else {
            st.pop(); // match with a previous '('
            if (st.empty()) {
                st.push(i); // reset base index if unbalanced
            } else {
                maxLen = max(maxLen, i - st.top());
            }
        }
    }

    return maxLen;
}

int main() {
    string s;
    cin >> s;

    cout << longestBalancedSubstring(s);
    return 0;
}
```

---

## 🏷️ Tags  
`🧮 Stack` | `🧵 Strings` | `📐 Two Pointers` | `💡 Logic Building`  

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

🧩 Keep cracking balanced problems—your logic muscle just got stronger 💪  
Next up: More brain-boosting patterns coming in Day 19!