# 🏦 DSA Sheet – Problem 6: 🔐 Min Stack

## 🎯 Problem Level  
**Hard**

---


## 🧩 Background  

This is a **variation of the stack design problem** often seen in:
- **Financial trading systems**
- **Min/max query optimization**
- **Stack-based real-time analysis**

Efficient stack design is crucial for operations that demand **O(1) retrieval of min elements** alongside regular stack functionality.

---

## 📝 Problem Statement  

Design a special stack data structure called `MinStack` that supports standard stack operations:  
- `push(val)` → Add element to the stack  
- `pop()` → Remove and return top of the stack  
- `top()` → Return top without removing  
- `getMin()` → Return the minimum element in the stack  

All operations must run in **O(1)** time complexity.  
This stack helps traders analyze price movements in real time and comply with regulations requiring **minimum stock price lookup** at any moment.

---

## 📥 Input Format  

- A list of operations in the format:  
```
[["push",5],["push",2],["push",4],["getMin"],["pop"],["getMin"]]
```

---

## 📤 Output Format  

- A list of results for each operation:  
  - `-1` for `push`  
  - The actual return value for `pop`, `top`, or `getMin`  
  - Return `-1` if a pop/top/getMin is called on an empty stack

---

## 🧪 Example  

### 🔹 Example Input  
```
[["push",5],["push",2],["push",4],["getMin"],["pop"],["getMin"]]
```

### 🔹 Example Output  
```
[-1,-1,-1,2,4,2]
```

### 🧠 Explanation  
- Push 5 → stack = [5], min = 5  
- Push 2 → stack = [5,2], min = 2  
- Push 4 → stack = [5,2,4], min = 2  
- getMin → 2  
- pop → 4 removed  
- getMin → still 2

---

## ⚙️ Constraints  
- `1 ≤ operations.length ≤ 10^5`  
- Operation values in range: `-10^9 ≤ val ≤ 10^9`  
- All string operations are among `"push"`, `"pop"`, `"top"`, `"getMin"`

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <vector>
#include <string>
#include <sstream>
#include <stack>
using namespace std;

// Implement the MinStack class
class MinStack {
private:
    stack<int> st;
    stack<int> minSt;

public:
    MinStack() {}

    void push(int val) {
        st.push(val);
        if (minSt.empty() || val <= minSt.top()) {
            minSt.push(val);
        } else {
            minSt.push(minSt.top());
        }
    }

    int pop() {
        if (st.empty()) return -1;
        int popped = st.top();
        st.pop();
        minSt.pop();
        return popped;
    }

    int top() {
        if (st.empty()) return -1;
        return st.top();
    }

    int getMin() {
        if (minSt.empty()) return -1;
        return minSt.top();
    }
};

// Please don't remove the code below
int main() {
    string input;
    getline(cin, input);

    MinStack minStack;
    vector<string> results;

    size_t start = input.find('[');
    size_t end = input.find_last_of(']');
    if (start != string::npos && end != string::npos) {
        string commandsStr = input.substr(start + 1, end - start - 1);
        size_t pos = 0;
        while ((pos = commandsStr.find('[', pos)) != string::npos) {
            size_t endPos = commandsStr.find(']', pos);
            string command = commandsStr.substr(pos + 1, endPos - pos - 1);

            string operation;
            int value = 0;
            size_t commaPos = command.find(',');

            if (commaPos != string::npos) {
                operation = command.substr(0, commaPos);
                operation = operation.substr(1, operation.length() - 2);
                value = stoi(command.substr(commaPos + 1));
            } else {
                operation = command;
                operation = operation.substr(1, operation.length() - 2);
            }

            if (operation == "push") {
                minStack.push(value);
                results.push_back("-1");
            } else if (operation == "pop") {
                results.push_back(to_string(minStack.pop()));
            } else if (operation == "top") {
                results.push_back(to_string(minStack.top()));
            } else if (operation == "getMin") {
                results.push_back(to_string(minStack.getMin()));
            }

            pos = endPos + 1;
        }
    }

    cout << "[";
    for (size_t i = 0; i < results.size(); i++) {
        cout << results[i];
        if (i < results.size() - 1) {
            cout << ",";
        }
    }
    cout << "]";

    return 0;
}
```

---

## 🏷️ Tags  
`📦 Stack` | `💡 Design Problem` | `⏱️ O(1) Min Lookup` | `📉 Financial Analysis`

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
