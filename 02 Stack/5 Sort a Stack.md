# 🔐 DSA Sheet – Problem 5: 🔻 Sort a Stack

## 🧠 Problem Level  
**Hard**

---

## 🧩 Background  

You're designing a **document management system** where files are processed in a **LIFO** manner — like a stack of papers.  
But there's a twist:  
- You can **only access the top** of the stack.
- You can **only use push, pop**, and an **extra temporary stack**.

This problem mirrors constraints found in:
- **Hardware memory management**
- **Network packet buffers**
- **Compiler stack operations**

Mastering this improves your control over **data movement with constraints** and enhances understanding of **stack-based sorting algorithms**.

---

## 📝 Problem Statement  

You are given a stack of integers. Your task is to **sort the stack in ascending order** (smallest at the top) using only the following operations:
- `push(x)` — Push element onto stack  
- `pop()` — Remove top element  
- One **extra temporary stack** is allowed

Return the **sorted stack** as a vector with the top element first.

---

## 📥 Input Format  

- A single array represented as a string like: `[5,2,9,1,5]`  
  (where the **first** element is the **top** of the stack)

---

## 📤 Output Format  

- A sorted array with **smallest element at top**, in vector format

---

## 🧪 Example  

### 🔹 Example Input  
```
[5,2,9,1,5]
```

### 🔹 Example Output  
```
[1,2,5,5,9]
```

### 🧠 Explanation  
The input stack has 5 on top.  
You are allowed only:
- stack operations  
- one temporary stack

Final stack (top to bottom): 1 → 2 → 5 → 5 → 9

---

## ⚙️ Constraints  
- `1 ≤ stack.length ≤ 10^5`  
- `-10^9 ≤ stack[i] ≤ 10^9`  

---

## 💻 C++ Solution  

```cpp
#include <bits/stdc++.h>
using namespace std;

// Function to sort a stack using only push, pop and a temp stack
vector<int> sortStack(vector<int>& stack) {
    if (stack.size() <= 1) return stack;

    vector<int> tempStack;

    while (!stack.empty()) {
        int temp = stack.back();
        stack.pop_back();

        // Move elements from tempStack back to stack until correct position found
        while (!tempStack.empty() && tempStack.back() > temp) {
            stack.push_back(tempStack.back());
            tempStack.pop_back();
        }

        tempStack.push_back(temp);
    }

    // Reverse to get the top element at the beginning of the vector
    reverse(tempStack.begin(), tempStack.end());
    return tempStack;
}

int main() {
    string input;
    getline(cin, input);

    // Remove brackets from input
    input = input.substr(1, input.length() - 2);
    stringstream ss(input);
    string num;
    vector<int> stack;

    // Parse comma-separated input values
    while (getline(ss, num, ',')) {
        stack.push_back(stoi(num));
    }

    // Sort the stack
    vector<int> result = sortStack(stack);

    // Print the result
    cout << "[";
    for (int i = 0; i < result.size(); i++) {
        cout << result[i];
        if (i < result.size() - 1) cout << ",";
    }
    cout << "]";

    return 0;
}
```

---

## 🏷️ Tags  
`🧱 Stack` | `📊 Sorting with Constraints` | `↔️ Temp Stack Logic` | `🧠 Monotonic Thinking`

---

## 👨‍💻 Author  

### 🚀 **Darshan Vasani**  
Code Mentor | Stack Tactician | C++ Series Creator  

### 🌐 Connect  
- 🌍 [dpvasani56.vercel.app](https://dpvasani56.vercel.app)  
- 💬 [Topmate.io](https://topmate.io/dpvasani56)  
- 💻 [GitHub](https://github.com/dpvasani)  
- 🧵 [Twitter](https://x.com/vasanidarshan56)

--- 
