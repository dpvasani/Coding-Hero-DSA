# 📌 DSA Sheet – 6: Circular Kadane - Day 30

## 🎯 Problem Level  
**Medium**

---

## 🧩 Background  

You are given an array where each element represents the strength of a kid sitting in a circular arrangement. You need to find the maximum possible sum of contiguous elements, considering that the elements are arranged in a circle. This means that the first element is adjacent to the last element, and you can select subarrays that might "wrap around" from the end to the start of the array.

The goal is to determine the maximum possible sum of any contiguous subarray, considering the circular nature of the array.

---

## 📝 Problem Statement  

Given an array of `N` integers representing the strength of kids sitting in a circle, find the maximum sum of a contiguous subarray (team) of these values.

### Input  
- The first line contains an integer `N` (the number of kids).
- The second line contains `N` space-separated integers representing the strength of each kid.

### Output  
- A single integer representing the maximum possible strength of the team that can be formed.

---

## 📥 Example  

### 🔹 Testcase 1  
```
Input:
5
1 2 3 4 5

Output:
15
```

**Explanation**  
In this case, the maximum sum is obtained by selecting all the elements of the array, as there are no negative numbers.

---

### 🔹 Testcase 2  
```
Input:
5
1 -2 3 4 -1

Output:
10
```

**Explanation**  
In this case, the maximum sum is obtained by selecting the subarray [3, 4, -1] which gives the sum of 10.

---

## ⚙️ Constraints  
- \(1 \leq N \leq 10^5\)
- \( -10^4 \leq arr[i] \leq 10^4 \)

---

## 💻 C++ Solution  

This problem can be solved using an extension of Kadane's algorithm to handle circular arrays. The approach can be broken into two parts:

1. **Normal Kadane’s Algorithm**: This is used to find the maximum sum of a subarray in the non-circular case.
2. **Circular Kadane’s Algorithm**: This is done by calculating the total sum of the array and subtracting the minimum sum subarray from it. The idea is that a circular subarray can be represented by taking the total sum of the array and subtracting a non-circular subarray (i.e., the subarray that has the minimum sum).

### Steps:
1. Find the maximum subarray sum using Kadane’s algorithm (non-circular).
2. Find the minimum subarray sum using Kadane’s algorithm (modified).
3. Compute the total sum of the array.
4. The result is the maximum of:
   - The result from the normal Kadane's algorithm (non-circular).
   - The total sum minus the minimum sum subarray (for circular case).
   
### Edge case:
- If all the numbers are negative, the total sum minus the minimum sum might lead to zero or negative values, so we should avoid considering the entire array being the minimum subarray in that case.

### C++ Code:

```cpp
#include <bits/stdc++.h>
using namespace std;

int Solve(int N, vector<int>& arr) {
    // Helper function for Kadane's algorithm to find max sum subarray
    auto kadane = [](vector<int>& arr) {
        int max_sum = arr[0], current_sum = arr[0];
        for (int i = 1; i < arr.size(); i++) {
            current_sum = max(arr[i], current_sum + arr[i]);
            max_sum = max(max_sum, current_sum);
        }
        return max_sum;
    };

    // Find the normal maximum subarray sum (Kadane's algorithm)
    int max_normal = kadane(arr);
    
    // Find the total sum of the array and the minimum subarray sum
    int total_sum = 0;
    int min_subarray_sum = arr[0], current_min_sum = arr[0];
    
    for (int i = 0; i < N; i++) {
        total_sum += arr[i];
        current_min_sum = min(arr[i], current_min_sum + arr[i]);
        min_subarray_sum = min(min_subarray_sum, current_min_sum);
    }

    // If the total sum equals the minimum subarray sum, all elements are negative
    // In that case, we cannot remove any element, so return the max_normal
    if (total_sum == min_subarray_sum) {
        return max_normal;
    }

    // For circular case, subtract the minimum subarray sum from the total sum
    int max_circular = total_sum - min_subarray_sum;

    // Return the maximum of both non-circular and circular cases
    return max(max_normal, max_circular);
}

int main() {
    int N;
    cin >> N;
    vector<int> arr(N);
    for (int i = 0; i < N; i++) {
        cin >> arr[i];
    }

    cout << Solve(N, arr) << endl;

    return 0;
}
```

---

## 🧠 Explanation  

### Key Concepts:
1. **Kadane’s Algorithm**:
   - The main idea is to track the sum of the current subarray while iterating through the array. If the sum becomes negative, we reset it to 0 since it would reduce the potential sum of subsequent subarrays.
   
2. **Circular Array Handling**:
   - A circular subarray can be considered as the array where you may wrap around. If you calculate the sum of all elements and subtract the minimum subarray sum, it effectively simulates the circular nature by considering the array wrapping from the end to the beginning.

3. **Edge Case Handling**:
   - If all elements are negative, the total sum minus the minimum subarray sum would be 0 or a negative number, which is not valid. Hence, we return the result of the normal Kadane’s algorithm in such a case.

### Time Complexity:
- **Kadane’s Algorithm** runs in \(O(N)\), and since we are applying it twice (once for maximum and once for minimum), the overall complexity remains \(O(N)\), which is efficient for \(N \leq 10^5\).

---

## 🏷️ Tags  
`📚 Dynamic Programming` | `🔢 Kadane’s Algorithm` | `🧩 Circular Arrays`

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

🌟 Solve the Circular Kadane problem efficiently with Kadane’s algorithm extension for circular arrays! 🌟

---