# 🔐 DSA Sheet – Problem 1: Password Strength Checker

## 🛡️ Problem Background  

You are a **Cybersecurity Engineer** at **ChaiCode**, working on an API to evaluate the strength of user passwords during signup. A **strong password** is crucial to keep user accounts safe from hackers! 🦸‍♂️💻  

---

## 📜 Problem Statement  

Your task is to **implement a function** that checks if a given password meets the following **strength criteria**:  

### ✅ Strength Criteria  

1️⃣ **Minimum length** of **8 characters**  
2️⃣ At least **one uppercase** letter (`A-Z`)  
3️⃣ At least **one lowercase** letter (`a-z`)  
4️⃣ At least **one digit** (`0-9`)  
5️⃣ At least **one special character** (e.g., `!@#$%^&*()-_=+[]{}|;:'",.<>?/`~`)  

---

## 📝 Input Format  

📌 A **single string** `password`:  
- `1 <= length(password) <= 1000`  
- Consists of **printable ASCII characters**  

## 🎯 Output Format  

🔹 Return `"Strong"` if the password meets **all criteria**  
🔹 Return `"Weak"` otherwise  

---

## 📌 Example  

### 🔹 Input  
```cpp
Password123!
```

### 🔹 Output  
```cpp
Strong
```

### 🧐 Explanation  
✔️ Length ≥ 8  
✔️ Contains an **uppercase** letter  
✔️ Contains a **lowercase** letter  
✔️ Contains a **digit**  
✔️ Contains a **special character**  

---

## ⚡ Constraints  

- `1 <= length of password <= 1000`  
- Password may include **any printable ASCII characters**  

---

## 💻 C++ Solution  

```cpp
#include <iostream>
using namespace std;

string passwordStrengthChecker(const string &password) {
    if (password.length() < 8) return "Weak";

    bool hasUpper = false, hasLower = false, hasDigit = false, hasSpecial = false;
    string specialChars = "!@#$%^&*()-_=+[]{}|;:'\",.<>?/`~";

    for (char ch : password) {
        if (isupper(ch)) hasUpper = true;
        else if (islower(ch)) hasLower = true;
        else if (isdigit(ch)) hasDigit = true;
        else if (specialChars.find(ch) != string::npos) hasSpecial = true;
    }

    return (hasUpper && hasLower && hasDigit && hasSpecial) ? "Strong" : "Weak";
}

// please don't remove this code
int main() {
    string password;
    while (getline(cin, password)) {
        cout << passwordStrengthChecker(password);
    }
    return 0;
}
```

---

## 🏷️ Tags  

`🔠 Strings` | `✅ Validation` | `🔍 Simulation` | `🔢 Character Checking`  

---

## 👨‍💻 Author  

### 🚀 **Darshan Vasani**  
💡 **Full-Stack Developer | Software Engineer | Mentor**   

### 🔗 Connect with me! 🌍  
🌐 **Portfolio:** [dpvasani56.vercel.app](https://dpvasani56.vercel.app/)  
🐙 **GitHub:** [github.com/dpvasani](https://github.com/dpvasani)  
💼 **LinkedIn:** [linkedin.com/in/dpvasani56](https://www.linkedin.com/in/dpvasani56/)  
🌳 **Linktree:** [linktr.ee/dpvasani56](https://linktr.ee/dpvasani56)  
🎓 **Credly:** [credly.com/users/dpvasani55](https://www.credly.com/users/dpvasani55/)  
🐦 **Twitter:** [x.com/vasanidarshan56](https://x.com/vasanidarshan56)  
📢 **Topmate:** [topmate.io/dpvasani56](https://topmate.io/dpvasani56)  

---

🚀 **Follow me for more cool DSA problems & solutions!** 🌟  
--
