# 📌 DSA Sheet – 3:🎲 Dice Game - Day 29

## 🎯 Problem Level  
**Medium**

---

## 🧩 Background  

Anirudh and Akash are playing a fun dice game. The goal is to determine how many different ways Anirudh can roll a standard six-sided die (with faces numbered from 1 to 6) one or more times so that the sum of the numbers rolled equals exactly `n`. Each roll adds a number between 1 and 6 to the total, and the order of the rolls matters (i.e., rolling 1 then 2 is different from rolling 2 then 1).

---

## 📝 Problem Statement  

You are given a target sum `n`. You need to find the number of different ways Anirudh can roll a standard six-sided die such that the sum of the numbers rolled equals exactly `n`. Each roll contributes a number from 1 to 6 to the sum, and the order of rolls matters. The result must be given modulo \(10^9 + 7\).

### Input  
- A single integer `n`, representing the target sum.

### Output  
- A single integer — the number of possible ways to reach the sum `n` by rolling the die, modulo \(10^9 + 7\).

---

## 📥 Example  

### 🔹 Testcase 1  
```
Input:
4

Output:
8
```

**Explanation**  
The 8 ways to achieve a sum of 4 are:
- 1 + 1 + 1 + 1
- 1 + 1 + 2
- 1 + 2 + 1
- 2 + 1 + 1
- 2 + 2
- 1 + 3
- 3 + 1
- 4

---

## ⚙️ Constraints  
- \(1 \leq n \leq 1000\)

---

## 💻 C++ Solution  

```cpp
#include <bits/stdc++.h>
using namespace std;

int countDiceCombinations(int n) {
    const int mod = 1e9 + 7;
    vector<int> dp(n + 1);
    dp[0] = 1;  // Base case: There is 1 way to get sum 0 (not rolling any dice)

    // Fill the dp array for sums from 1 to n
    for (int k = 1; k <= n; k++) {
        int sum = 0;
        // Check all dice faces (1 to 6)
        for (int i = 1; i <= 6; i++) {
            if (k - i >= 0) {  // Only consider valid indices
                sum = (sum + dp[k - i]) % mod;
            }
        }
        dp[k] = sum;  // Update dp[k] with the computed sum
    }
    
    return dp[n];  // Return the number of ways to reach sum n
}

int main() {
    int n;
    cin >> n;  // Input the target sum
    
    cout << countDiceCombinations(n) << endl;  // Output the result
    
    return 0;
}
```

---

## 🧠 Explanation  

1. **Dynamic Programming Array `dp`:**
   - The `dp` array stores the number of ways to achieve each sum from 0 to `n`.
   - `dp[k]` represents the number of ways to get the sum `k` using dice rolls.
   
2. **Base Case:**
   - `dp[0] = 1`, meaning there's exactly one way to get a sum of 0: not rolling any dice.
   
3. **Filling the DP Array:**
   - For each possible sum `k` from 1 to `n`, we calculate the total number of ways to form that sum by adding any number from 1 to 6 (the faces of the die).
   - For each dice face `i`, if subtracting `i` from `k` results in a valid sum (`k - i >= 0`), we add `dp[k - i]` to `dp[k]`.
   
4. **Modulo Operation:**
   - Since the result can be large, we take the answer modulo \(10^9 + 7\) to avoid overflow and adhere to the problem constraints.

---

## 🏷️ Tags  
`🎲 Dynamic Programming` | `📅 Recursion` | `🔢 Counting` | `🧩 Combinatorics` | `🔢 Time Complexity`

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

🌟 Solve the dice game problem using dynamic programming! 🌟

---