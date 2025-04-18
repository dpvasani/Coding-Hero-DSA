# 📌 DSA Sheet – 1 : ❓ String Compression  
## 🎯 Problem Level  
**Medium**
---

## 🧩 Background  

You are working on a **file compression algorithm**. Part of this process involves implementing a basic **string compression** technique. The goal is to replace **consecutive repeated characters** with the character followed by its **frequency**.

However, the twist is:  
🔸 If the compressed version **is not smaller** than the original string, return the **original string**.

This is a great problem to test your **string manipulation**, **looping logic**, and **edge case** handling.

---

## 📝 Problem Statement  

Given a string `s` made up of uppercase and lowercase English letters, compress it using the following rules:

- Replace each sequence of repeating characters with that character followed by the **count of repetitions**.
- If the resulting compressed string is **not shorter** than the original, return the **original string**.

---

## 📥 Input Format  
- A single string `s`  
  (Contains only lowercase or uppercase English letters)

---

## 📤 Output Format  
- Return the compressed version of the string, or the original string if the compressed version is not shorter.

---

## 🧪 Example  

### 🔹 Testcase 1  
```
Input:  
aabcccccaaa

Output:  
a2b1c5a3
```

**Explanation:**  
- `"aa"` → `"a2"`  
- `"b"` → `"b1"`  
- `"ccccc"` → `"c5"`  
- `"aaa"` → `"a3"`  

The compressed version is `"a2b1c5a3"` which is shorter than the original, so it's returned.

---

## ⚙️ Constraints  
- `1 ≤ s.length() ≤ 10⁴`  
- `s` contains only English letters (a–z, A–Z)

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <string>
using namespace std;

// Function to compress the string
string compressString(string s) {
    string compressed = "";
    int count = 1;

    for (int i = 1; i <= s.length(); ++i) {
        if (i < s.length() && s[i] == s[i - 1]) {
            count++;
        } else {
            compressed += s[i - 1] + to_string(count);
            count = 1;
        }
    }

    return compressed.length() < s.length() ? compressed : s;
}

int main() {
    string s;
    cin >> s;
    cout << compressString(s);
    return 0;
}
```

---

## 🏷️ Tags  
`🧵 Strings` | `🔁 Looping` | `🧠 Logic Building` | `🧪 Edge Cases`  

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

🔥 Keep grinding. Consistency beats perfection. See you on Day 19!