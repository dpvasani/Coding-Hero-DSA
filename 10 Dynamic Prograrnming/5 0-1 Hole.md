# 📌 DSA Sheet – 5: 0-1 Hole - Day 30

## 🎯 Problem Level  
**Medium**

---

## 🧩 Background  

You are given an array of `N` integers. Your task is to consider all possible contiguous subarrays of this array and determine the maximum possible sum that can be achieved by removing any number of elements (possibly none) from the subarrays. The problem is a variation of the **maximum subarray sum** problem, where you can modify the subarray by removing some elements to maximize the sum.

---

## 📝 Problem Statement  

Given an array of `N` integers, you are to find the maximum possible sum of any subarray by possibly removing some elements. You need to find the maximum obtainable sum from any such subarray.

### Input  
- The first line contains an integer `N`, the length of the array.
- The second line contains `N` integers, representing the array `arr`.

### Output  
- A single integer representing the maximum sum of any subarray that can be obtained by removing some elements.

---

## 📥 Example  

### 🔹 Testcase 1  
```
Input:
6
1 2 -3 4 5 -6

Output:
9
```

**Explanation**  
In this case, the maximum sum is obtained by removing the negative numbers. The subarray [4, 5] gives the maximum sum of 9.

---

## ⚙️ Constraints  
- \(1 \leq N \leq 10^5\)
- \( -10^4 \leq arr[i] \leq 10^4 \)

---

## 💻 C++ Solution  

This problem can be solved using a variation of **Kadane's Algorithm**. Kadane’s algorithm is used to find the maximum sum of a contiguous subarray in linear time \(O(N)\). In this variation, we allow the possibility of removing some elements, meaning that instead of just considering the sum of elements in a subarray, we also consider skipping negative numbers to maximize the sum.

### Approach:
- Traverse the array, maintaining a running sum.
- If the running sum becomes negative, reset it to 0 because any negative running sum will decrease the sum of the following subarray.
- Keep track of the maximum sum encountered during the traversal.

### Algorithm:

1. Initialize `max_sum` to a very small number (or negative infinity).
2. Traverse through the array:
   - For each element, add it to a running sum.
   - If the running sum becomes negative, reset it to 0.
   - Update `max_sum` with the greater of the current `max_sum` and the running sum.
   
3. Return `max_sum`.

```cpp
#include <bits/stdc++.h>
using namespace std;

int Solve(int N, vector<int>& arr) {
    int max_sum = INT_MIN;  // Initialize to a very small number
    int current_sum = 0;    // Running sum of the subarray
    
    for (int i = 0; i < N; i++) {
        current_sum += arr[i];
        
        // If the current sum is negative, reset it to 0
        if (current_sum < 0) {
            current_sum = 0;
        }
        
        // Update the maximum sum encountered
        max_sum = max(max_sum, current_sum);
    }
    
    return max_sum;
}

int main() {
    int N;
    cin >> N;  // Input the length of the array
    
    vector<int> arr(N);
    for (int i = 0; i < N; i++) {
        cin >> arr[i];  // Input the elements of the array
    }
    
    cout << Solve(N, arr) << endl;  // Output the result
    
    return 0;
}
```

---

## 🧠 Explanation  

### Key Concepts:
1. **Kadane's Algorithm**:
   - The core idea of Kadane’s algorithm is to keep a running sum of the current subarray. If the sum becomes negative, it’s discarded (since adding negative sums will reduce the total). If the sum is positive, it may contribute to a larger subarray sum.
   
2. **Handling Negative Elements**:
   - The sum is reset whenever it becomes negative, as continuing to add negative sums would decrease the total possible sum. This allows us to "remove" the negative subarrays and continue with the next possible subarray.

3. **Time Complexity**:
   - The solution runs in \(O(N)\) time, which is efficient enough for \(N \leq 10^5\).

---

## 🏷️ Tags  
`📚 Dynamic Programming` | `🧩 Kadane’s Algorithm` | `🔢 Subarrays`

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

🌟 Solve the 0-1 Hole problem using Kadane's algorithm for an efficient solution! 🌟

---