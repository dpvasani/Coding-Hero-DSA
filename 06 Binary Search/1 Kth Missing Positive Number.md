# 📌 DSA Sheet – Problem 1: ❓ Kth Missing Positive Number  
## 🎯 Problem Level  
**Medium**

---

## 🧩 Background  

Given a sorted array of **distinct positive integers** and an integer `k`, return the **kth positive integer** that is **missing from this array**.

Instead of brute-force traversal, we can **use binary search** to efficiently determine the position where at least `k` numbers have been missed, using the logic:  
- At any index `i`, the count of missing numbers is `arr[i] - (i + 1)`  
Using this, we perform a binary search for the smallest index such that missing ≥ `k`.

---

## 📝 Problem Statement  

You are given a sorted array `arr[]` of `n` distinct positive integers and a number `k`. Your task is to find the `k`th positive integer that is **missing** from this array.

---

## 📥 Input Format  
- Two integers `n` and `k`  
- Followed by `n` space-separated integers of the array `arr[]`

```
Input:  
n k  
arr[0] arr[1] ... arr[n-1]
```

---

## 📤 Output Format  
- A single integer representing the `kth` missing positive number.

---

## 🧪 Example  

### 🔹 Example 1  
```
Input:  
5 5  
2 3 4 7 11

Output:  
9
```

**Explanation:**  
Missing numbers = [1, 5, 6, 8, 9, 10, ...]  
The 5th missing number is **9**

---

## ⚙️ Constraints  
- `1 ≤ n ≤ 1000`  
- `1 ≤ k ≤ 1000`  
- `1 ≤ arr[i] ≤ 10^4`  
- Elements in `arr[]` are strictly increasing

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <vector>
using namespace std;

int findKthMissing(vector<int>& arr, int k) {
    int left = 0, right = arr.size() - 1;

    while (left <= right) {
        int mid = left + (right - left) / 2;
        int missing = arr[mid] - (mid + 1); // how many numbers are missing before arr[mid]

        if (missing < k)
            left = mid + 1;
        else
            right = mid - 1;
    }

    return left + k;  // formula derived from binary search positioning
}

int main() {
    int n, k;
    cin >> n >> k;
    vector<int> arr(n);

    for (int i = 0; i < n; ++i) {
        cin >> arr[i];
    }

    cout << findKthMissing(arr, k);
    return 0;
}
```

---

## 🏷️ Tags  
`📚 Binary Search` | `📈 Arrays` | `🔢 Math` | `🎯 Missing Elements Logic`

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
