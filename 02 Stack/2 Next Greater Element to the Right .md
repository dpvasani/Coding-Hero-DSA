# 🔐 DSA Sheet – Problem 2: ⚡ Next Greater Element to the Right
## 🧠 Problem Level  
**Medium**

---

## 🧩 Background  

This problem is a classic **interview favorite**, often used to test your understanding of:
- **Stack-based** approaches
- **Array traversal**
- Efficient **O(n)** solutions

Used in **real-world applications** such as:
- **Stock span problems**
- **Code analyzers**
- **Pattern detection** and more

---

## 📝 Problem Statement  

Given an array of integers, for each element, find the **next greater element** that appears to the **right**.  
If no such element exists, return **-1** for that position.

---

## 📥 Input Format  

- A single array represented as a string like: `[4,5,2,25]`

---

## 📤 Output Format  

- An array where each index contains the next greater element or -1

---

## 🧪 Example  

### 🔹 Example Input  
```
[4,5,2,25]
```

### 🔹 Example Output  
```
[5,25,25,-1]
```

### 🧠 Explanation  
- 4 → next greater is **5**  
- 5 → next greater is **25**  
- 2 → next greater is **25**  
- 25 → no greater element → **-1**

---

## ⚙️ Constraints  
- `1 ≤ arr.length ≤ 10^5`  
- `-10^9 ≤ arr[i] ≤ 10^9`

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <vector>
#include <string>
#include <stack>
using namespace std;

// Function to find the next greater element for each array item
vector<int> nextGreaterElement(vector<int>& arr) {
    int n = arr.size();
    vector<int> result(n, -1); // Initialize result with -1
    stack<int> st; // Store indices

    for (int i = 0; i < n; i++) {
        while (!st.empty() && arr[i] > arr[st.top()]) {
            int idx = st.top();
            st.pop();
            result[idx] = arr[i];
        }
        st.push(i);
    }

    return result;
}

// Please don't remove the code below
int main() {
    string input;
    getline(cin, input);
    
    vector<int> arr;
    size_t pos = input.find('[');
    size_t end = input.find(']');
    
    if (pos != string::npos && end != string::npos) {
        string arrStr = input.substr(pos + 1, end - pos - 1);
        size_t start = 0;
        size_t commaPos = arrStr.find(',');
        
        while (commaPos != string::npos) {
            string numStr = arrStr.substr(start, commaPos - start);
            arr.push_back(stoi(numStr));
            start = commaPos + 1;
            commaPos = arrStr.find(',', start);
        }
        
        if (start < arrStr.length()) {
            string numStr = arrStr.substr(start);
            arr.push_back(stoi(numStr));
        }
    }
    
    vector<int> result = nextGreaterElement(arr);
    
    cout << "[";
    for (size_t i = 0; i < result.size(); i++) {
        cout << result[i];
        if (i < result.size() - 1) {
            cout << ",";
        }
    }
    cout << "]";
    
    return 0;
}
```

---

## 🏷️ Tags  
`📦 Stack` | `📈 Array Processing` | `🔥 Next Greater Element` | `🧠 Interview Patterns`

---

## 👨‍💻 Author  

### 🚀 **Darshan Vasani**  
Full-Stack Dev | DSA Mentor | C++ Sheet Builder  

### 🔗 Stay Connected  
- 🌍 [dpvasani56.vercel.app](https://dpvasani56.vercel.app)  
- 💡 [Topmate Sessions](https://topmate.io/dpvasani56)  
- 🧑‍💻 [GitHub](https://github.com/dpvasani)  
- 🧵 [Twitter](https://x.com/vasanidarshan56)

---
