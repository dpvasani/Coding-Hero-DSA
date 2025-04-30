# 📌 DSA Sheet – 28 : 🍷 Fine Wine

## 🎯 Problem Level  
**Medium**

---

## 🧩 Background  

You are given `N` wines, each with a price for the year it was made. The price of a wine increases each year. In the first year, you can sell any wine and after that, you can only sell one wine per year. Each time you sell a wine, the profit is multiplied by the year. Your goal is to maximize the total profit over `N` years.

The key challenge is to decide the order in which you sell the wines in order to maximize the profit.

---

## 📝 Problem Statement  

Given `N` wines with prices for each year, find the maximum profit you can achieve by selling them one by one, considering that:
- You sell one wine per year, and the price of the wine is multiplied by the year of sale.
- You can sell any wine in the first year, but after that, you can only sell one wine each year.
- You must find the order of wine sales that maximizes the total profit.

The answer should be modulo \(10^9 + 7\).

---

## 📥 Input Format  
- The first line contains a single integer `N` — the number of wines.
- The second line contains `N` integers representing the prices of the wines.

---

## 📤 Output Format  
- A single integer — the maximum profit modulo \(10^9 + 7\).

---

## 🧪 Example  

### 🔹 Testcase 1  
```
Input:
3
2 3 5

Output:
26
```

**Explanation**  
- In the first year, sell the wine priced 5 → profit = 5 * 3 = 15
- In the second year, sell the wine priced 3 → profit = 3 * 2 = 6
- In the third year, sell the wine priced 2 → profit = 2 * 1 = 2  
Total profit = 15 + 6 + 2 = 26

---

## ⚙️ Constraints  
- \(1 \leq N \leq 1000\)
- Prices are positive integers.

---

## 💻 C++ Solution  

```cpp
#include <bits/stdc++.h>
using namespace std;

using ll = long long;
const ll mod = 1e9 + 7;

int Solve(int N, vector<int>& Prices) {
    vector<vector<ll>> dp(N, vector<ll>(N, -1));  // dp[i][j] stores the max profit for wine from i to j
    
    // Base case: when only one bottle is sold, it's sold in the N-th year
    for (int i = 0; i < N; i++) {
        dp[i][i] = (1LL * N * Prices[i]) % mod;
    }

    // Fill the dp table for subarrays of size 2 to N
    for (int size = 2; size <= N; size++) {  // size of the subarray
        for (int i = 0; i + size - 1 < N; i++) {
            int j = i + size - 1;  // End of the subarray
            int year = N - size + 1;  // Year when we sell this wine
            
            // Option 1: Sell wine at the beginning (i)
            ll option1 = (Prices[i] * year % mod + dp[i + 1][j] % mod + mod) % mod;
            
            // Option 2: Sell wine at the end (j)
            ll option2 = (Prices[j] * year % mod + dp[i][j - 1] % mod + mod) % mod;
            
            // Take the maximum of both options
            dp[i][j] = max(option1, option2);
        }
    }

    // Return the result for the entire array
    return (int)(dp[0][N - 1] % mod);
}

int main() {
    int N;
    cin >> N;  // Input the number of wines (or years)
    
    vector<int> Prices(N);
    for (auto& p : Prices) {
        cin >> p;  // Input the wine prices for each year
    }

    cout << Solve(N, Prices) << endl;  // Output the maximum profit
    
    return 0;
}
```

---

## 🏷️ Tags  
`🧩 Dynamic Programming` | `💡 Optimization` | `💰 Maximum Profit` | `🔢 Recursion` | `📅 Time Complexity`

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

🌟 Solve the fine wine problem using dynamic programming! 🌟

---