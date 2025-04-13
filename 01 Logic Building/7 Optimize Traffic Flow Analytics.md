# 🧩 DSA Sheet – Problem 7: Optimize Traffic Flow Analytics

## 🎯 Problem Level  
**Easy**

---

## 📚 Problem Background  

As part of the **Spring Smart City Initiative**, you're building a module to analyze traffic data for multiple roads. To detect potential **congestion trends**, you must identify the **maximum traffic flow** recorded over any **`k` consecutive intervals**.

This helps the city predict high-traffic patterns and implement real-time traffic optimization strategies 🚦.

---

## 📝 Problem Statement  

You are given:
- An array `trafficFlow[]` representing the traffic count at each time interval.
- An integer `k` which denotes the number of consecutive intervals to consider.  

Find the **maximum sum** of traffic flow over any **`k` consecutive intervals**.

---

## 📥 Input Format  

- A list of integers: `trafficFlow`  
- An integer: `k`, the size of the sliding window

---

## 📤 Output Format  

- A single integer representing the **maximum traffic flow sum** over any `k` consecutive intervals.

---

## 🧪 Example  

### 🔹 Input  
```
[[10, 20, 30, 40, 50], 3]
```

### 🔹 Output  
```
120
```

### 🧠 Explanation  
Window Sums:
- [10, 20, 30] → 60  
- [20, 30, 40] → 90  
- [30, 40, 50] → 120  
➡️ Max = **120**

---

## ⚙️ Constraints  

- `1 ≤ trafficFlow.length ≤ 10^5`  
- `0 ≤ trafficFlow[i] ≤ 10^3`  
- `1 ≤ k ≤ trafficFlow.length`

Use **sliding window** for optimal O(n) performance.

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <vector>
#include <sstream>
#include <string>

using namespace std;

int maxTrafficFlow(const vector<int>& trafficFlow, int k) {
    int maxSum = 0, currentSum = 0;

    // Compute the sum of the first 'k' elements
    for (int i = 0; i < k; i++) {
        currentSum += trafficFlow[i];
    }
    maxSum = currentSum;

    // Slide the window from index 'k' to the end
    for (size_t i = k; i < trafficFlow.size(); i++) {
        currentSum += trafficFlow[i] - trafficFlow[i - k];
        maxSum = max(maxSum, currentSum);
    }

    return maxSum;
}

int main() {
    string input;
    getline(cin, input);

    // Parse input manually
    input = input.substr(1, input.size() - 1); // Remove outer brackets
    size_t splitIndex = input.find_last_of(',');

    string arrayPart = input.substr(0, splitIndex);
    int k = stoi(input.substr(splitIndex + 1));

    vector<int> trafficFlow;
    stringstream ss(arrayPart.substr(1, arrayPart.size() - 2)); // Remove nested brackets
    string item;

    while (getline(ss, item, ',')) {
        trafficFlow.push_back(stoi(item));
    }

    int result = maxTrafficFlow(trafficFlow, k);
    cout << result;

    return 0;
}
```

---

## 🏷️ Tags  
`📊 Sliding Window` | `⚡ Optimization` | `📈 Maximum Subarray Sum` | `📶 Real-time Analytics`

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
