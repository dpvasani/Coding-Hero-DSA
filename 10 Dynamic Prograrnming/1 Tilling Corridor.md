# 📌 DSA Sheet – 1 : 🏙️ Tilling Corridor

## 🎯 Problem Level  
**Easy**

---

## 🧩 Background  

You are given an infinite supply of tiles, each of size 2x1. These tiles can be placed vertically or horizontally. Your task is to find the number of distinct ways to completely cover a 2xN corridor using only these tiles, ensuring no overlaps and no gaps. The answer can be very large, so you need to return it modulo 1,000,000,007.

---

## 📝 Problem Statement  

You are given an integer `N`, which represents the length of the corridor.  
Your task is to determine the number of unique ways to tile the 2xN corridor using 2x1 tiles. The answer should be returned modulo \(10^9 + 7\).

---

## 📥 Input Format  
- A single integer `N` — the length of the corridor.  

---

## 📤 Output Format  
- A single integer — the number of unique ways to tile the corridor, modulo \(10^9 + 7\).

---

## 🧪 Example  

### 🔹 Testcase 1  
```
Input:
3

Output:
3
```

**Explanation**  
For N = 3, the distinct ways to tile the corridor are:  
1. Place one tile horizontally at the bottom and one vertically on top.
2. Place two tiles vertically.
3. Place one tile horizontally at the top and one vertically at the bottom.

---

## ⚙️ Constraints  
- \(1 \leq N \leq 1000\)

---

## 💻 C++ Solution  

```cpp
#include <bits/stdc++.h>
using namespace std;

const int MOD = 1e9 + 7; // Modulo constant

int Solve(int N) {
    if (N == 1) return 1;  // Base case: 1 way to tile a 2x1 grid
    if (N == 2) return 2;  // Base case: 2 ways to tile a 2x2 grid
    
    vector<int> dp(N + 1); // DP array to store the results for each length
    
    // Initialize the base cases
    dp[1] = 1;
    dp[2] = 2;
    
    // Fill the DP array for lengths from 3 to N
    for (int i = 3; i <= N; ++i) {
        dp[i] = (dp[i - 1] + dp[i - 2]) % MOD;  // Apply recurrence relation
    }
    
    return dp[N];  // Return the result for the 2xN corridor
}

int main() {
    int N;
    cin >> N;  // Input the length of the corridor
    
    cout << Solve(N) << endl;  // Output the result
    
    return 0;
}
```

---

## 🏷️ Tags  
`🏗️ Dynamic Programming` | `🧩 Recursion` | `💡 Modulo Arithmetic` | `🔢 Fibonacci-like` | `🚀 Optimization`

---

## 👨‍💻 Author  

### 🚀 **Darshan Vasani**  
💡 **Full-Stack Developer | Software Engineer | Mentor**  

### 🔗 Connect with me! 🌍  
🌐 **Portfolio:** [dpvasani56.vercel.app](https://dpvasani56.vercel.app)  
🐙 **GitHub:** [github.com/dpvasani](https://github.com/dpvasani)  
💼 **LinkedIn:** [linkedin.com/in/dpvasani56](https://www.linkedin.com/in/dpvasani56/)  
🌳 **Linktree:** [linktr.ee/dpvasani56](https://linktr.ee/dpvasani56)  
🎓 **Credly:** [credly.com/users/dpvasani57](https://www.credly.com/users/dpvasani57/)  
🐦 **Twitter:** [x.com/vasanidarshan56](https://x.com/vasanidarshan56)  
📢 **Topmate:** [topmate.io/dpvasani56](https://topmate.io/dpvasani56)

--- 

🌟 Solve the corridor tiling problem with dynamic programming! 🌟

---