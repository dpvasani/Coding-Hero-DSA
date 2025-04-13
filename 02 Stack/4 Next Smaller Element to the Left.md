# 🔐 DSA Sheet – Problem 4: 🔻 Next Smaller Element to the Left

## 🧠 Problem Level  
**Easy**

---

## 🧩 Background  

This problem is a variation of the **Next Greater Element** problem but focuses on finding the smaller element to the **left** instead. The **monotonic stack** approach is ideal for solving this efficiently.  

Common use cases include:
- **Stock market analysis**
- **Histogram problems**
- **Array scanning** where you're looking for the next or previous smaller/greater element

Mastering this problem will deepen your understanding of **stack manipulation** and improve your ability to handle problems with **limited access to data**.

---

## 📝 Problem Statement  

Implement a function that finds the **previous smaller element** for each element in an array. The **previous smaller element** is the first smaller element that appears to the **left**. If no such element exists, return **-1**.

---

## 📥 Input Format  

- A single array represented as a string like: `[4,5,2,10,8]`

---

## 📤 Output Format  

- An array where each index contains the previous smaller element or **-1**

---

## 🧪 Example  

### 🔹 Example Input  
```
[4,5,2,10,8]
```

### 🔹 Example Output  
```
[-1,4,-1,2,2]
```

### 🧠 Explanation  
- **4** → no smaller element to the left → **-1**
- **5** → previous smaller element is **4**
- **2** → no smaller element to the left → **-1**
- **10** → previous smaller element is **2**
- **8** → previous smaller element is **2**

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
using namespace std;

// Function to find the previous smaller element for each element
vector<int> previousSmallerElement(vector<int>& arr) {
    int n = arr.size();
    vector<int> result(n, -1);  // Initialize result array with -1 (default value)
    stack<int> st;              // Stack to store elements

    // Iterate through each element in the array
    for (int i = 0; i < n; i++) {
        // While stack is not empty and the current element is smaller or equal to the element at the top of the stack
        while (!st.empty() && arr[st.top()] >= arr[i]) {
            st.pop(); // Pop elements from the stack as they can't be the previous smaller for any future element
        }

        // If the stack is not empty, the top element is the previous smaller element
        if (!st.empty()) {
            result[i] = arr[st.top()];
        }

        // Push the current element's index onto the stack
        st.push(i);
    }

    return result;
}

int main() {
    string input;
    getline(cin, input);
    
    // Parse the input array
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
        
        // Handle the last number
        if (start < arrStr.length()) {
            string numStr = arrStr.substr(start);
            arr.push_back(stoi(numStr));
        }
    }
    
    // Get the result
    vector<int> result = previousSmallerElement(arr);
    
    // Output the result
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
`🧱 Stack` | `🔙 Previous Smaller Element` | `↔️ Array Scanning` | `🧠 Monotonic Stack`

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
