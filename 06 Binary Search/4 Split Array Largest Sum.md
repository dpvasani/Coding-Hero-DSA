# 📌 DSA Sheet – Problem 4: ❓ Split Array Largest Sum  
## 🎯 Problem Level  
**Medium**

---

## 🧩 Background  

You're tasked with splitting an array of integers into **m non-empty continuous subarrays**. Your objective is to **minimize the largest sum** among these subarrays. This problem is crucial in scenarios like load balancing, resource distribution, and parallel processing where the objective is to distribute tasks as evenly as possible.

The challenge is to find the most efficient way to partition the array to achieve the smallest possible **maximum subarray sum**.

---

## 📝 Problem Statement  

You are given an integer array `nums` and an integer `m`.  
Split the array into `m` **non-empty continuous subarrays** such that the **maximum sum** of any subarray is **minimized**. Return that minimized largest sum.

---

## 📥 Input Format  
- First line: Two integers `n` and `m` — size of the array and number of subarrays.  
- Second line: `n` integers denoting the array elements.

---

## 📤 Output Format  
- A single integer representing the minimized largest sum among the `m` subarrays after splitting.

---

## 🧪 Example  

### 🔹 Example 1  
```
Input:  
7 2  
5 10 8  

Output:  
14
```

**Explanation:**  
You need to split the array into 3 subarrays:  
- First subarray: `[7, 2, 5]` (sum = 14)  
- Second subarray: `[10]` (sum = 10)  
- Third subarray: `[8]` (sum = 8)  

The largest subarray sum is `14`, which is the **minimum possible maximum** across all valid splits.

---

## ⚙️ Constraints  
- 1 ≤ n ≤ 1000  
- 1 ≤ m ≤ min(50, n)  
- 0 ≤ nums[i] ≤ 10⁶

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
#include <numeric> // For accumulate
using namespace std;

// Helper function to check if we can split into <= m parts with given maxSumAllowed
bool canSplit(const vector<int>& nums, int m, int maxSumAllowed) {
    int subarrays = 1, currentSum = 0;
    for (int num : nums) {
        if (currentSum + num > maxSumAllowed) {
            subarrays++;
            currentSum = num;
            if (subarrays > m) return false;
        } else {
            currentSum += num;
        }
    }
    return true;
}

// Main function to implement
int splitArray(vector<int>& nums, int m) {
    int left = *max_element(nums.begin(), nums.end());
    int right = accumulate(nums.begin(), nums.end(), 0);
    int answer = right;

    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (canSplit(nums, m, mid)) {
            answer = mid;
            right = mid - 1;
        } else {
            left = mid + 1;
        }
    }

    return answer;
}

int main() {
    int n, m;
    cin >> n >> m;
    
    vector<int> nums(n);
    for (int i = 0; i < n; i++) {
        cin >> nums[i];
    }
    
    cout << splitArray(nums, m);
    return 0;
}
```

---

## 🏷️ Tags  
`📚 Binary Search on Answer` | `🧮 Greedy Partitioning` | `📊 Array Manipulation` | `💡 Optimization`

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