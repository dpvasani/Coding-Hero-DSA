
# 🧩 DSA Sheet – Problem 12: 🧠 The Professor's Heist Window Challenge

## 🎯 Problem Level  
**Medium**

---

## 🧩 Background  

During the daring heist at the **Bank of Spain**, the Professor must **analyze the cash transportation schedule**. The heist depends on exploiting the **maximum cash transported in any fixed time window of `k` hours**.

Your task is to help the Professor compute this value quickly using the **Sliding Window Technique**. This ensures flawless planning, without any unnecessary delays or miscalculations.

---

## 📝 Problem Statement  

You are given:
- An array of integers representing the **cash transported during each of `n` hours**.
- An integer `k`, the size of the time window.

Return the **maximum amount of cash transported in any window of `k` consecutive hours**.

---

## 📥 Input Format  
- First line: Two integers `n` and `k`  
- Second line: `n` space-separated integers representing cash moved each hour

---

## 📤 Output Format  
- A single integer: the **maximum cash** transported in any `k`-hour window

---

## 🧪 Example  

### 🔹 Example 1  
**Input**  
```
6 3  
10 20 30 40 50 60
```

**Output**  
```
150
```

**Explanation**  
Window sums:  
- 10+20+30 = 60  
- 20+30+40 = 90  
- 30+40+50 = 120  
- 40+50+60 = **150** ← ✅ Maximum  

---

## ⚙️ Constraints  

- `1 ≤ n ≤ 10^5`  
- `1 ≤ k < n`  
- `1 ≤ cash[i] ≤ 10^4`

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <vector>
using namespace std;

// Function to calculate max cash in any k-hour window
int maxCashInWindow(vector<int>& cash, int k) {
    int n = cash.size();
    if (n < k) return 0;

    // Step 1: Compute sum of the first window
    int windowSum = 0;
    for (int i = 0; i < k; i++) {
        windowSum += cash[i];
    }

    int maxSum = windowSum;

    // Step 2: Slide the window across the array
    for (int i = k; i < n; i++) {
        windowSum = windowSum - cash[i - k] + cash[i];
        maxSum = max(maxSum, windowSum);
    }

    return maxSum;
}

int main() {
    int n, k;
    cin >> n >> k;
    
    vector<int> cash(n);
    for (int i = 0; i < n; i++) {
        cin >> cash[i];
    }
    
    cout << maxCashInWindow(cash, k);
    return 0;
}
```

---

## 🏷️ Tags  
`🔁 Sliding Window` | `🔢 Arrays` | `📈 Maximum Subarray Sum` | `🚨 Heist Optimization`

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
