# 🔐 DSA Sheet – Problem 3: 🔻 Next Smaller Element to the Right

## 🧠 Problem Level  
**Medium**

---

## 🧩 Background  

This is a **variation of the next greater element** problem and is commonly used in:
- **Stock market algorithms**
- **Histogram area problems**
- **Monotonic stack patterns**

Efficient solutions here improve your grasp on **greedy + stack** approaches.

---

## 📝 Problem Statement  

Implement a function that finds the **next smaller element** for each element in an array.  
The **next smaller element** is the first smaller element that appears to the **right**.  
If no such element exists, use **-1**.

---

## 📥 Input Format  

- A single array represented as a string like: `[4,5,2,10,8]`

---

## 📤 Output Format  

- An array where each index contains the next smaller element or -1

---

## 🧪 Example  

### 🔹 Example Input  
```
[4,5,2,10,8]
```

### 🔹 Example Output  
```
[2,2,-1,8,-1]
```

### 🧠 Explanation  
- 4 → next smaller is **2**  
- 5 → next smaller is **2**  
- 2 → no smaller element → **-1**  
- 10 → next smaller is **8**  
- 8 → no smaller → **-1**

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

// Function to find the next smaller element for each element
vector<int> nextSmallerElement(vector<int>& arr) {
    int n = arr.size();
    vector<int> result(n, -1); // Default value is -1
    stack<int> st;             // Stack to store indices

    for (int i = 0; i < n; i++) {
        while (!st.empty() && arr[i] < arr[st.top()]) {
            int idx = st.top();
            st.pop();
            result[idx] = arr[i]; // Current element is the next smaller for arr[idx]
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
    
    vector<int> result = nextSmallerElement(arr);
    
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
`🧱 Stack` | `↘️ Next Smaller Element` | `🔁 Array Scanning` | `🧠 Monotonic Stack`

---

## 👨‍💻 Author  

### 🚀 **Darshan Vasani**  
Code Mentor | Stack Enthusiast | C++ Series Creator  

### 🌐 Connect  
- 🌍 [dpvasani56.vercel.app](https://dpvasani56.vercel.app)  
- 💬 [Topmate.io](https://topmate.io/dpvasani56)  
- 💻 [GitHub](https://github.com/dpvasani)  
- 🧵 [Twitter](https://x.com/vasanidarshan56)

---
