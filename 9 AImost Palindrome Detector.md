
# 🧩 DSA Sheet – Problem 9: Almost Palindrome Detector

## 🎯 Problem Level  
**Easy**

---

## 📚 Problem Background  

Variable naming is an essential part of writing readable and maintainable code. Companies like JetBrains and Microsoft have implemented **smart suggestions** in their IDEs to enhance code readability and development efficiency. For instance, suggesting **palindromic variable names** (e.g., "level", "radar") makes it easier for developers to choose meaningful names.

You are tasked with building a feature in a **smart code editor** to detect if a string can become a palindrome by removing **at most one character**. A **palindrome** is a word or sequence that reads the same backward as forward.

---

## 📝 Problem Statement  

Given:
- A string `s` (1 <= length of `s` <= 10^5), consisting only of lowercase letters ('a' to 'z').

Your task is to determine if the string can become a **palindrome** by removing **at most one character**.  

Return:
- `true` if the string can be turned into a palindrome by removing at most one character.
- `false` otherwise.

---

## 📥 Input Format  

- A string `s` (1 <= length of `s` <= 10^5), containing only lowercase alphabets.

---

## 📤 Output Format  

- **`true`** if the string can become a palindrome by removing at most one character.
- **`false`** otherwise.

---

## 🧪 Example  

### 🔹 Example 1  

**Input**  
```
raceecar
```

**Output**  
```
true
```

**Explanation**  
By removing the middle 'e', the string becomes "racecar", which is a palindrome.

### 🔹 Example 2  

**Input**  
```
abccba
```

**Output**  
```
true
```

**Explanation**  
This string is already a palindrome, so no characters need to be removed.

---

## ⚙️ Constraints  

- `1 ≤ length(s) ≤ 10^5`
- The input string `s` contains only lowercase alphabets.

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <string>
using namespace std;

// Helper function to check if a substring is a palindrome
bool isPalindrome(const string& s, int left, int right) {
    while (left < right) {
        if (s[left] != s[right]) {
            return false;
        }
        left++;
        right--;
    }
    return true;
}

// Main function to check if the string can be a palindrome by removing at most one character
bool canBePalindrome(string s) {
    int left = 0, right = s.length() - 1;

    while (left < right) {
        if (s[left] == s[right]) {
            left++;
            right--;
        } else {
            // Try removing either the character at left or right
            return isPalindrome(s, left + 1, right) || isPalindrome(s, left, right - 1);
        }
    }
    
    return true; // It's already a palindrome
}

int main() {
    string s;
    cin >> s;
    
    // Output YES if the string can become a palindrome by removing one character
    cout << (canBePalindrome(s) ? "YES" : "NO");
    return 0;
}
```

---

## 🏷️ Tags  
`🧑‍💻 String Manipulation` | `🧠 Palindrome` | `🔧 Algorithm` | `📝 Code Optimization`

---

## 👨‍💻 Author  

### 🚀 **Darshan Vasani**  
💡 Full-Stack Developer | Mentor | DSA & System Design Enthusiast  

### 🌐 Connect with Me  
- 🌐 Website: [dpvasani56.vercel.app](https://dpvasani56.vercel.app)  
- 💼 LinkedIn: [@dpvasani56](https://linkedin.com/in/dpvasani56)  
- 🧑‍💻 GitHub: [@dpvasani](https://github.com/dpvasani)  
- 🗂️ Linktree: [linktr.ee/dpvasani56](https://linktr.ee/dpvasani56)  
- 📞 Topmate: [topmate.io/dpvasani56](https://topmate.io/dpvasani56)

---
