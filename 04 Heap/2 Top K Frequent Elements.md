# 🔐 DSA Sheet – Problem 2: 📊 Top K Frequent Elements

## 🎯 Problem Level  
**Medium**

---

## 🧩 Background  

As a **data analyst** working with large datasets, you may need to quickly identify the most common items for trend analysis. This problem introduces the use of a **Min-Heap** to efficiently track the top **k** frequent elements in an array, ensuring that the time complexity is better than **O(n log n)**.

---

## 📝 Problem Statement  

Given an integer array and an integer `k`, find the **k most frequent elements** in the array.  
- The result should be sorted by frequency, from highest to lowest.
- If two elements have the same frequency, they can be returned in any order.
- The solution should be better than **O(n log n)** time complexity.

---

## 📥 Input Format  

- **nums**: An array of integers, e.g., `[1, 1, 1, 2, 2, 3]`  
- **k**: An integer representing how many top frequent elements to return (e.g., `2`).

---

## 📤 Output Format  

- An array of the **k most frequent elements**.

---

## 🧪 Example  

### 🔹 Example Input  
```
[1,1,1,2,2,3] | 2
```

### 🔹 Example Output  
```
[1, 2]
```

### 🧠 Explanation  
- `1` appears **3** times, and `2` appears **2** times, so these are the most frequent elements.
- The output is `[1, 2]`.

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
#include <unordered_map>
#include <sstream>
#include <string>
#include <algorithm>
using namespace std;

// Function to find the top K frequent elements using a min-heap
vector<int> topKFrequent(vector<int>& nums, int k) {
    // Step 1: Build a frequency map
    unordered_map<int, int> freqMap;
    for (int num : nums) {
        freqMap[num]++;
    }
    
    // Step 2: Min-heap to keep track of the k most frequent elements
    priority_queue<pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>>> minHeap;
    
    // Step 3: Push elements into the heap, maintaining only the top k frequent elements
    for (auto& entry : freqMap) {
        minHeap.push({entry.second, entry.first});
        if (minHeap.size() > k) {
            minHeap.pop();
        }
    }

    // Step 4: Extract the k most frequent elements
    vector<int> result;
    while (!minHeap.empty()) {
        result.push_back(minHeap.top().second);
        minHeap.pop();
    }

    // Step 5: Return the result in correct order (sorted by frequency)
    reverse(result.begin(), result.end());
    return result;
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
    vector<int> res = topKFrequent(nums, k);
    cout << "[";
    for (int i = 0; i < res.size(); ++i) {
        if (i) cout << ",";
        cout << res[i];
    }
    cout << "]";
    return 0;
}
```

---

## 🏷️ Tags  
`🛠️ Heap` | `🧠 Min-Heap` | `⚙️ Frequency Map` | `⏱️ Time Optimization`

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
