# 🧩 DSA Sheet – Problem 8: Challenge

## 🎯 Problem Level  
**Medium**

---

## 📚 Problem Background  

In financial applications, **stock market analysis** is crucial to help traders make better trading decisions. Traders often need to track the **peak stock prices** within a specific time window. For example, during a trading day, they may want to see the highest stock price for the last `k` minutes.

To help with this, you're tasked with implementing a feature that calculates the **maximum stock price** for any **sliding window** of size `k`.

---

## 📝 Problem Statement  

You are given:
- A list of integers `prices[]` representing stock prices at regular intervals.
- An integer `k`, the size of the sliding window (number of consecutive intervals).

Your task is to return a list where each element represents the **maximum stock price** in the respective sliding window.

---

## 📥 Input Format  

- A list of integers: `prices[]`  
- An integer `k`, the size of the sliding window

---

## 📤 Output Format  

- A list of integers representing the **maximum price** in each sliding window.

---

## 🧪 Example  

### 🔹 Input  
```
prices = [10, 7, 12, 5, 8, 15]
k = 3
```

### 🔹 Output  
```
[12, 12, 12, 15]
```

### 🧠 Explanation  
Window-wise max:
- [10, 7, 12] → 12  
- [7, 12, 5] → 12  
- [12, 5, 8] → 12  
- [5, 8, 15] → 15  

So, the result is `[12, 12, 12, 15]`.

---

## ⚙️ Constraints  

- `1 ≤ prices.length ≤ 10^5`  
- `1 ≤ k ≤ prices.length`  
- `0 ≤ prices[i] ≤ 10^4`

---

## 💻 C++ Solution  

```cpp
#include <vector>
#include <deque>
#include <iostream>

using namespace std;

// Intuition:
// As we are using a sliding window, we need to keep track of the maximum price in the current window.
// Think of it like a queue; we need to keep track of the maximum price in the current window.
// We can use a deque to store the indices of the prices in the current window.
// We can use a vector to store the result.
// We can iterate through the prices and, for each price, remove the indices of the prices that are smaller than the current price.
// We add the current price's index to the deque.
// If the current index is greater than or equal to k - 1, we can add the price at the front of the deque to the result.

// Time Complexity: O(n) — Each index is added and removed from the deque at most once.
// Space Complexity: O(n) — The deque stores at most 'n' indices.

vector<int> maxInRollingWindow(vector<int>& prices, int k) {
    vector<int> result;  // To store the maximums of each window
    deque<int> dq;  // Deque to store indices of prices

    // Traverse the prices array
    for (int i = 0; i < prices.size(); i++) {
        // Remove indices that are not in the current window
        if (!dq.empty() && dq.front() <= i - k) {
            dq.pop_front();
        }

        // Remove indices of elements smaller than the current element
        while (!dq.empty() && prices[dq.back()] < prices[i]) {
            dq.pop_back();
        }

        // Add the current element's index to the deque
        dq.push_back(i);

        // Once we have processed at least 'k' elements, we add the max to the result
        if (i >= k - 1) {
            result.push_back(prices[dq.front()]);  // The element at the front is the maximum
        }
    }

    return result;
}

int main() {
    int n, k;
    cin >> n >> k;  // Read number of prices and window size

    vector<int> prices(n);
    for (int i = 0; i < n; i++) {
        cin >> prices[i];  // Read prices into the vector
    }

    vector<int> result = maxInRollingWindow(prices, k);  // Get the result from the function
    
    // Output the result
    for (int i = 0; i < result.size(); i++) {
        if (i == result.size() - 1) {
            cout << result[i];  // Print last element without a space
        } else {
            cout << result[i] << " ";  // Print other elements with a space
        }
    }

    return 0;
}
```

---

## 🏷️ Tags  
`📊 Sliding Window` | `📈 Stock Market` | `⚡ Optimization` | `💹 Real-time Analysis`

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
