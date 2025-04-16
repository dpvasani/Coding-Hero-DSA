# 📌 DSA Sheet – Problem X: ❓ Finding Peak Internet Traffic  
## 🎯 Problem Level  
**Medium**

---

## 🧩 Background  

As a network analyst at a major tech company, you're monitoring internet traffic patterns across data centers. The traffic pattern shows a distinct trend where traffic increases, reaches a peak, and then decreases. By analyzing these patterns, you aim to identify the peak traffic volume during a 24-hour period.

Your goal is to find the index of the peak element, where the traffic stops increasing and starts decreasing. This is critical for understanding when the network experiences its highest load and optimizing it accordingly.

---

## 📝 Problem Statement  

You are given an array representing internet traffic volumes at different time points during a day. The traffic volumes follow a specific pattern: they increase, reach a peak, and then decrease. The task is to find the index of the peak element in the array.  

### Input:  
- A list of integers representing traffic volume at different time points (in Gbps).
- The array is guaranteed to have a single peak element (mountain shape).

### Output:  
- The index of the peak element.

---

## 📥 Input Format  
- A single integer `n` — the number of traffic samples.
- A list of `n` integers representing the traffic volume at each time point.

---

## 📤 Output Format  
- A single integer representing the index of the peak element in the array.

---

## 🧪 Example  

### 🔹 Example 1  
```
Input:  
7  
1 3 5 7 6 4 2  

Output:  
3
```

**Explanation:**  
The peak value is `7`, which is at index 3 in the array.

### 🔹 Example 2  
```
Input:  
5  
10 20 30 40 50  

Output:  
4
```

**Explanation:**  
The peak value is `50`, which is at index 4 in the array.

### 🔹 Example 3  
```
Input:  
5  
50 40 30 20 10  

Output:  
0
```

**Explanation:**  
The peak value is `50`, which is at index 0 in the array.

---

## ⚙️ Constraints  
- The array will have at least one element.
- If there are multiple peaks with the same value, return the index of any one of them.
- The solution must run in **O(log n)** time complexity, where `n` is the number of elements in the array.

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <vector>
using namespace std;

int findPeakTraffic(vector<int>& traffic) {
    int left = 0, right = traffic.size() - 1;
    
    while (left <= right) {
        int mid = left + (right - left) / 2;
        
        // Check if mid is the peak
        if ((mid == 0 || traffic[mid - 1] <= traffic[mid]) && 
            (mid == traffic.size() - 1 || traffic[mid + 1] <= traffic[mid])) {
            return mid;
        }
        
        // If the right neighbor is greater, move to the right half
        else if (mid < traffic.size() - 1 && traffic[mid + 1] > traffic[mid]) {
            left = mid + 1;
        }
        // Otherwise, move to the left half
        else {
            right = mid - 1;
        }
    }
    
    return -1; // This line will never be reached due to the given constraints
}

int main() {
    int n;
    cin >> n;
    
    vector<int> traffic(n);
    for (int i = 0; i < n; i++) {
        cin >> traffic[i];
    }
    
    int peakIndex = findPeakTraffic(traffic);
    cout << peakIndex;
    
    return 0;
}
```

---

## 🏷️ Tags  
`📚 Binary Search` | `📈 Array` | `⏳ Optimization` | `🕰️ Peak Finding`

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

🔥 **Stay tuned for more clean and optimized DSA patterns!** 💡

---