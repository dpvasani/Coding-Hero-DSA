# 📌 DSA Sheet – 2 : ❓ Valid Anagram Substrings  
## 🎯 Problem Level  
**Medium**

---

## 🧩 Background  

You are given a **pattern string** `p` and a **text string** `t`.  
Your task is to **find all the starting indices** of substrings in `t` that are **anagrams** of `p`.

🧠 An anagram is a **rearrangement** of letters of a word using **all characters exactly once**.  
Example: `"listen"` and `"silent"` are anagrams.

This is a classic **sliding window + frequency map** problem and often appears in real-world scenarios like **searching patterns** in DNA sequences, **log analysis**, and **spam detection**.

---

## 📝 Problem Statement  

Given two strings `p` (pattern) and `t` (text), return a list of all starting indices (0-indexed) in `t` where the substring is an anagram of `p`.

---

## 📥 Input Format  
- First line: A lowercase string `p` (pattern)  
- Second line: A lowercase string `t` (text)

---

## 📤 Output Format  
- A list of integers (space-separated), each representing a starting index of a substring in `t` that is an anagram of `p`.

---

## 🧪 Example  

### 🔹 Testcase 1  
```
Input:  
abc  
cbaebabacd  

Output:  
0 6
```

**Explanation:**  
- Substring `t[0:3]` = `"cba"` is an anagram of `"abc"`  
- Substring `t[6:9]` = `"bac"` is an anagram of `"abc"`

---

## ⚙️ Constraints  
- `1 ≤ p.length() ≤ t.length() ≤ 10⁴`  
- `p` and `t` consist of lowercase English letters only

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <vector>
#include <string>
using namespace std;

// Function to find starting indices of anagram substrings
vector<int> findAnagrams(string p, string t) {
    vector<int> result;
    int m = p.size(), n = t.size();
    if (m > n) return result;

    vector<int> pCount(26, 0), windowCount(26, 0);

    // Frequency count for pattern
    for (char c : p)
        pCount[c - 'a']++;

    // Sliding window across text
    for (int i = 0; i < n; ++i) {
        windowCount[t[i] - 'a']++; // include right char

        if (i >= m) {
            windowCount[t[i - m] - 'a']--; // remove left char
        }

        if (windowCount == pCount) {
            result.push_back(i - m + 1);
        }
    }

    return result;
}

int main() {
    string p, t;
    cin >> p >> t;

    vector<int> indices = findAnagrams(p, t);
    for (int index : indices) {
        cout << index << " ";
    }
    return 0;
}
```

---

## 🏷️ Tags  
`🔁 Sliding Window` | `🧵 Strings` | `📊 Frequency Counting` | `🧠 Pattern Matching`  

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

🧩 Keep solving and keep growing! Up next: Day 19 challenges!