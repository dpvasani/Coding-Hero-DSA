# 🔐 DSA Sheet – Problem 1: 🧾 Bracket Validation for Code Editor — C++ Challenge

## 🎯 Problem Level  
**Easy**

---


## 🧩 Background  

You're building a **code editor** feature like in **VS Code** or **IntelliJ** where the system must validate that all **brackets are properly balanced**. This is critical for:
- Code **linters**
- Syntax **highlighters**
- **Compilers** and **interpreters**

The rules are simple but strict:
1. **Open brackets** must be **closed by the same type**  
2. Brackets must be **closed in the correct order**  
3. Every **closing bracket** must have a **corresponding open bracket**

---

## 📝 Problem Statement  

Given a string `s` containing only characters:  
`'('`, `')'`, `'{'`, `'}'`, `'['`, and `']'`  
Write a function that returns **true** if the input string is a **valid sequence of brackets**, otherwise **false**.

---

## 📥 Input Format  

- A single string containing only bracket characters  
- No whitespace or other symbols

---

## 📤 Output Format  

- Print `true` or `false` based on whether the input is valid

---

## 🧪 Example  

### 🔹 Example Input 1  
```
()[{}]
```

### 🔹 Example Output 1  
```
true
```

### 🔹 Example Input 2  
```
([)]
```

### 🔹 Example Output 2  
```
false
```

### 🧠 Explanation  
- The first string is fully balanced and properly nested  
- The second has correct count, but **order is wrong**

---

## ⚙️ Constraints  
- `1 ≤ s.length ≤ 10^4`  
- Characters are only from the set: `{}`, `[]`, `()`

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <string>
#include <stack>
using namespace std;

// Function to validate brackets
bool isValidParentheses(string s) {
    stack<char> st;
    
    for (char ch : s) {
        if (ch == '(' || ch == '{' || ch == '[') {
            st.push(ch);
        } else if (ch == ')' || ch == '}' || ch == ']') {
            if (st.empty()) return false;
            char top = st.top();
            if ((ch == ')' && top != '(') ||
                (ch == '}' && top != '{') ||
                (ch == ']' && top != '[')) {
                return false;
            }
            st.pop();
        }
    }
    
    return st.empty();
}

// Please don't remove the code below
int main() {
    string input;
    getline(cin, input);
    
    bool result = isValidParentheses(input);
    cout << (result ? "true" : "false");
    
    return 0;
}
```

---

## 🏷️ Tags  
`🧮 Stack` | `🧑‍💻 IDE Development` | `🧰 Compiler Tools` | `🧱 Data Structures`

---

## 👨‍💻 Author  

### 🚀 **Darshan Vasani**  
💡 **Full-Stack Developer | Software Engineer | Mentor**    

### 🔗 Connect with me! 🌍  
🌐 **Portfolio:** [dpvasani56.vercel.app](https://dpvasani56.vercel.app/)  
🐙 **GitHub:** [github.com/dpvasani](https://github.com/dpvasani)  
💼 **LinkedIn:** [linkedin.com/in/dpvasani56](https://www.linkedin.com/in/dpvasani56/)  
🌳 **Linktree:** [linktr.ee/dpvasani56](https://linktr.ee/dpvasani56)  
🎓 **Credly:** [credly.com/users/dpvasani57](https://www.credly.com/users/dpvasani57/)  
🐦 **Twitter:** [x.com/vasanidarshan56](https://x.com/vasanidarshan56)  
📢 **Topmate:** [topmate.io/dpvasani56](https://topmate.io/dpvasani56)  

---

🚀 **Follow me for more cool DSA problems & solutions!** 🌟  

---  
