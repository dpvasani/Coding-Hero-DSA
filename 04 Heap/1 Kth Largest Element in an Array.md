# 🔐 DSA Sheet – Problem 1: 🏆 Kth Largest Element in an Array
## 🎯 Problem Level  
**Medium**

---
## 🧩 Background  

In competitive programming and leaderboard systems, retrieving the **top K elements** efficiently without sorting the entire dataset is crucial. This problem introduces the concept of using a **Min-Heap** to solve the problem in **O(n log k)** time, which is faster than sorting the entire array (O(n log n)).

---

## 📝 Problem Statement  

Given an unsorted array of integers, implement a function that finds the **kth largest element**.  
The function should efficiently find the element that would be at the kth position if the array were sorted in descending order.  

The function must use a **Min-Heap** to achieve efficiency.  

---

## 📥 Input Format  

- **nums**: An array of integers, e.g., `[3, 2, 1, 5, 6, 4]`  
- **k**: An integer representing the position of the element to find (e.g., 2 for the 2nd largest element).

---

## 📤 Output Format  

- The kth largest element in the array as an integer.

---

## 🧪 Example  

### 🔹 Example Input  
```
[3, 2, 1, 5, 6, 4] | 2
```

### 🔹 Example Output  
```
5
```

### 🧠 Explanation  
After sorting the array: `[1, 2, 3, 4, 5, 6]`.  
The **2nd largest** element is **5**.

---

## ⚙️ Constraints  
- `1 ≤ nums.length ≤ 10^4`
- `1 ≤ k ≤ nums.length`
- `-10^4 ≤ nums[i] ≤ 10^4`

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <vector>
#include <queue>
#include <sstream>
#include <string>
using namespace std;

// Function to find the kth largest element using a min-heap
int findKthLargest(vector<int>& nums, int k) {
    // Min-heap to keep track of the k largest elements
    priority_queue<int, vector<int>, greater<int>> minHeap;

    // Iterate through the array
    for (int num : nums) {
        // Add the current element to the heap
        minHeap.push(num);

        // If the heap size exceeds k, remove the smallest element
        if (minHeap.size() > k) {
            minHeap.pop();
        }
    }

    // The root of the heap is the kth largest element
    return minHeap.top();
}

// Function to parse the input array from string format
vector<int> parseArray(const string& s) {
    vector<int> result;
    stringstream ss(s);
    char ch;
    int num;
    while (ss >> ch) {
        if ((ch >= '0' && ch <= '9') || ch == '-') {
            ss.putback(ch);
            ss >> num;
            result.push_back(num);
        }
    }
    return result;
}

int main() {
    string line;
    getline(cin, line);
    size_t sep = line.find('|');
    string arrPart = line.substr(0, sep);
    string kPart = line.substr(sep + 1);
    vector<int> nums = parseArray(arrPart);
    int k = stoi(kPart);
    cout << findKthLargest(nums, k);
    return 0;
}
```

---

## 🏷️ Tags  
`🛠️ Heap` | `⚙️ Min-Heap` | `⏱️ Time Optimization` | `🧠 Priority Queue`

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
