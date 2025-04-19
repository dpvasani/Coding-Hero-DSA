# 📌 DSA Sheet – 4 : ❓ String Rotations and Queries  
## 🎯 Problem Level  
**Medium**

---

## 🧩 Background  

You are given two strings: a **source string `s`** and a **target string `t`**.  
Your goal is to find the **minimum window substring in `s`** that contains **all the characters of `t`**, including **duplicates**.

This is a classic **sliding window** and **hashmap** based problem that appears in various **string manipulation** and **text-searching** tasks (like mini search engines, text parsers, or DNA sequence checks).

---

## 📝 Problem Statement  

Find the **minimum window substring** in `s` that contains **all characters of `t`**.  
- If **no such window exists**, return an empty string.  
- If multiple minimum-length windows exist, return **any one** of them.

---

## 📥 Input Format  
- First line: A string `s` (source string).  
- Second line: A string `t` (target string).  
- Both strings consist of **uppercase and lowercase English letters**.

---

## 📤 Output Format  
- Return the **minimum window substring** of `s` containing all characters of `t`.  
- If **no valid window** exists, return an **empty string**.

---

## 🧪 Example  

### 🔹 Testcase 1  
```
Input:  
ADOBECODEBANC  
ABC  

Output:  
BANC
```

**Explanation:**  
- The substring `"BANC"` is the **smallest window** in `s` that contains `'A'`, `'B'`, and `'C'`.  
- `"ADOBEC"` and `"ODEBANC"` also contain all characters but are longer than `"BANC"`.

---

## ⚙️ Constraints  
- `1 ≤ s.length, t.length ≤ 10⁵`  
- Strings contain only uppercase and lowercase letters.

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <string>
#include <unordered_map>
#include <algorithm>
#include <climits>
using namespace std;

// Function to find the minimum window in s that contains all characters of t
string minWindow(string s, string t) {
    if (s.size() < t.size()) return "";

    unordered_map<char, int> tFreq, windowFreq;
    for (char c : t) tFreq[c]++;

    int left = 0, right = 0;
    int required = tFreq.size();  // unique chars in t
    int formed = 0;               // how many chars of t matched in current window
    int minLen = INT_MAX, start = 0;

    while (right < s.size()) {
        char c = s[right];
        windowFreq[c]++;
        
        if (tFreq.count(c) && windowFreq[c] == tFreq[c])
            formed++;

        // Try to minimize the window
        while (left <= right && formed == required) {
            if (right - left + 1 < minLen) {
                minLen = right - left + 1;
                start = left;
            }

            windowFreq[s[left]]--;
            if (tFreq.count(s[left]) && windowFreq[s[left]] < tFreq[s[left]])
                formed--;
            left++;
        }
        right++;
    }

    return minLen == INT_MAX ? "" : s.substr(start, minLen);
}

int main() {
    string s, t;
    getline(cin, s);
    getline(cin, t);
    
    cout << minWindow(s, t);
    return 0;
}
```

---

## 🏷️ Tags  
`🔄 Sliding Window` | `🧵 Strings` | `📊 Hash Map` | `📈 Optimization`  

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
