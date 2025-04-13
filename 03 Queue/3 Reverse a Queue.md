# 🧩 DSA Sheet – Problem 3: Reverse a Queue

## 🎯 Problem Level  
**Medium**

---

## 📚 Problem Background  

This problem tests your ability to manipulate data structures, specifically queues and stacks. Reversing a queue using auxiliary data structures (like a stack) is a common technique. You will need to reverse the order of the elements in a queue, ensuring that the order is inverted.

---

## 📝 Problem Statement  

Given:
- A queue of integers, the task is to reverse the order of the elements in the queue.

The queue supports the following operations:
- `enqueue`: Add an element at the end using `push()`.
- `dequeue`: Remove an element from the front using `shift()`.
- `isEmpty`: Check if the queue is empty by checking the length.

You are required to reverse the queue, either using a stack or recursion as an auxiliary data structure. The function should return the reversed queue.

---

## 📥 Input Format  

- A queue of integers implemented as an array (e.g., `[1, 2, 3, 4, 5]`).

---

## 📤 Output Format  

- A reversed queue (e.g., `[5, 4, 3, 2, 1]`).

---

## 🧪 Example  

### 🔹 Example 1  

**Input**  
```
[10, 20, 30, 40, 50]
```

**Output**  
```
[50, 40, 30, 20, 10]
```

**Explanation**  
- The given queue `[10, 20, 30, 40, 50]` is reversed to `[50, 40, 30, 20, 10]`.

---

## ⚙️ Constraints  

- The queue can contain up to 1000 integers.

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <vector>
#include <queue>
#include <stack>
#include <string>
using namespace std;

// Function to reverse the queue
vector<int> reverseQueue(queue<int> q) {
    // Create a stack to reverse the queue
    stack<int> st;
    
    // Push all elements of the queue into the stack
    while (!q.empty()) {
        st.push(q.front());
        q.pop();
    }
    
    // Create a vector to store the reversed queue
    vector<int> result;
    
    // Pop elements from the stack and enqueue them into the result vector
    while (!st.empty()) {
        result.push_back(st.top());
        st.pop();
    }
    
    return result;
}

// Please don't remove the code below
int main() {
    string input;
    getline(cin, input);
    
    // Parse the input array
    queue<int> q;
    size_t pos = input.find('[');
    size_t end = input.find(']');
    
    if (pos != string::npos && end != string::npos) {
        string arrStr = input.substr(pos + 1, end - pos - 1);
        size_t start = 0;
        size_t commaPos = arrStr.find(',');
        
        while (commaPos != string::npos) {
            string numStr = arrStr.substr(start, commaPos - start);
            if (!numStr.empty()) {
                q.push(stoi(numStr));
            }
            start = commaPos + 1;
            commaPos = arrStr.find(',', start);
        }
        
        // Handle the last number
        if (start < arrStr.length()) {
            string numStr = arrStr.substr(start);
            if (!numStr.empty()) {
                q.push(stoi(numStr));
            }
        }
    }
    
    // Get the result
    vector<int> result = reverseQueue(q);
    
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
`🔢 Queue` | `🛠️ Stack` | `💡 Data Structure Manipulation` | `🔄 Reverse`

---

## 👨‍💻 Author  

### 🚀 **Darshan Vasani**  
💡 Full-Stack Developer | Mentor | DSA & System Design Enthusiast  

### 🌐 Connect with Me  
- 🌐 Website: [dpvasani56.vercel.app](https://dpvasani56.vercel.app)  
- 💼 LinkedIn: [@dpvasani56](https://linkedin.com/in/dpvasani56)  
- 🧑‍💻 GitHub: [@dpvasani](https://github.com/dpvasani)  
- 🗂️ Linktree: [linktr.ee/dpvasani56](https://linktr.ee/dpvasani56)  
- 📞 Topmate: [topmate.io/dpvasani56](https://topmate.io/dpvasani56)

---