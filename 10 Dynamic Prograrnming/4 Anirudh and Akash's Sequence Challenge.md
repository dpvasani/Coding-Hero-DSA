# 📌 DSA Sheet – 4: Anirudh and Akash's Sequence Challenge - Day 29

## 🎯 Problem Level  
**Medium**

---

## 🧩 Background  

Anirudh and Akash are fascinated by sequences of numbers. Akash presents Anirudh with a challenge: given a list of integers, can Anirudh determine the length of the longest increasing subsequence (LIS) in the list? A subsequence is a sequence derived from the original list by deleting some elements (possibly none) without changing the order of the remaining elements. The sequence is increasing if every element is strictly greater than the preceding element.

---

## 📝 Problem Statement  

You are given an integer `n` (the length of the list) and a list of integers `arr` representing the sequence. Your task is to determine the length of the longest increasing subsequence (LIS) in `arr`.

- A **subsequence** is a sequence derived from the original list by deleting some elements (possibly none) without changing the order of the remaining elements.
- A sequence is **increasing** if every element is strictly greater than the preceding element in the subsequence.

### Input  
- An integer `n`, the length of the list.
- A list of integers `arr` of length `n`.

### Output  
- The length of the longest increasing subsequence in `arr`.

---

## 📥 Example  

### 🔹 Testcase 1  
```
Input:
7
10 9 2 5 3 7 101

Output:
4
```

**Explanation**  
The longest increasing subsequence is [2, 3, 7, 101], which has length 4.

---

## ⚙️ Constraints  
- \(1 \leq arr[i] \leq 10^9\)

---

## 💻 C++ Solution  

This problem can be solved efficiently using dynamic programming with binary search (using `std::lower_bound`).

### Algorithm:  
- We maintain an array `dp` where `dp[i]` represents the smallest possible last element of an increasing subsequence of length `i+1`.
- For each number in the list, we perform a binary search using `std::lower_bound` to determine the position in `dp` where it can be inserted or replace an element. This ensures that the subsequence remains as long as possible.

### Time Complexity:
- Binary search for each element gives a time complexity of \(O(n \log n)\), where `n` is the size of the array.

```cpp
#include <bits/stdc++.h>
using namespace std;

int longestIncreasingSubsequence(int n, vector<int>& arr) {
    vector<int> dp;
    
    for (int i = 0; i < n; i++) {
        // Find the first element in dp that is greater than or equal to arr[i]
        auto it = lower_bound(dp.begin(), dp.end(), arr[i]);
        
        // If element is larger than all in dp, push it to the end
        if (it == dp.end()) {
            dp.push_back(arr[i]);
        } else {
            // Otherwise, replace the element at found position with arr[i]
            *it = arr[i];
        }
    }
    
    // The size of dp is the length of the longest increasing subsequence
    return dp.size();
}

int main() {
    int n;
    cin >> n;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    
    cout << longestIncreasingSubsequence(n, arr) << endl;
    return 0;
}
```

---

## 🧠 Explanation  

### Approach:
1. **Binary Search for Efficient Update**:
   - Use `lower_bound` to find the position of the element in `dp` where the current element of the array can be placed (i.e., either replacing an existing element or extending the subsequence).
   
2. **Updating `dp`**:
   - If the element is greater than all elements in `dp`, append it.
   - If there exists a smaller or equal element, replace it with the current element to maintain the smallest possible elements for subsequences of the same length.
   
3. **Final Result**:
   - The size of the `dp` array represents the length of the longest increasing subsequence.

---

## 🏷️ Tags  
`📚 Dynamic Programming` | `🔢 Binary Search` | `🧩 Sequence Analysis`

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

🌟 Implement the LIS problem using dynamic programming and binary search for an efficient solution! 🌟

---