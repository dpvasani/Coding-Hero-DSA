# 🧩 DSA Sheet – Problem 1: Implement Stack Using Queues

## 🎯 Problem Level  
**Medium**

---

## 📚 Problem Background  

You're tasked with building a **stack** using **queues**, which is a common interview question to test your understanding of data structures. A stack is a Last In First Out (LIFO) data structure, while a queue is a First In First Out (FIFO) data structure. In this task, you must simulate the operations of a stack (push, pop, top, isEmpty, and size) using queues.

The challenge here is to implement these stack operations using only the **enqueue** (add element to the end), **dequeue** (remove element from the front), and other queue-related operations.

---

## 📝 Problem Statement  

Given:
- A stack, which supports the following operations:
    - `push(element)`: Adds an element to the top of the stack.
    - `pop()`: Removes and returns the element at the top of the stack.
    - `top()`: Returns the element at the top of the stack without removing it.
    - `isEmpty()`: Returns `true` if the stack is empty, `false` otherwise.
    - `size()`: Returns the number of elements in the stack.

You need to implement this stack using **only queue operations** (enqueue, dequeue). The stack should support the operations efficiently using one or two queues.

---

## 📥 Input Format  

- A list of operations to perform on the stack.
- Each operation can be one of:
    - `push(element)`: Adds the element to the stack.
    - `pop()`: Removes and returns the element at the top.
    - `top()`: Returns the element at the top without removing it.
    - `isEmpty()`: Returns whether the stack is empty.
    - `size()`: Returns the number of elements in the stack.

---

## 📤 Output Format  

- Return the results for each operation:
    - For `push`, return `null`.
    - For `pop`, return the element that was removed.
    - For `top`, return the element at the top.
    - For `isEmpty`, return `true` or `false`.
    - For `size`, return the number of elements in the stack.

---

## 🧪 Example  

### 🔹 Example 1  

**Input**  
```
Operations: ["push", "push", "top", "pop", "size"]
Parameters: [[1], [2], [], [], []]
```

**Output**  
```
[null, null, 2, 2, 1]
```

**Explanation**  
- `push(1)` adds `1` to the stack.
- `push(2)` adds `2` to the stack.
- `top()` returns `2` (top element).
- `pop()` removes and returns `2`.
- `size()` returns `1` as there is only `1` left in the stack.

---

## ⚙️ Constraints  

- 1 ≤ operations.length ≤ 1000
- -10⁹ ≤ element ≤ 10⁹

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <queue>
#include <vector>
#include <string>
using namespace std;

// Please implement this class only
class StackUsingQueues {
private:
    queue<int> q1;
    queue<int> q2;

public:
    StackUsingQueues() {
        // Initialize empty queues
    }

    void push(int x) {
        // Step 1: Push to q2
        q2.push(x);

        // Step 2: Push all q1 elements into q2
        while (!q1.empty()) {
            q2.push(q1.front());
            q1.pop();
        }

        // Step 3: Swap q1 and q2
        swap(q1, q2);
    }

    int pop() {
        if (q1.empty()) return -1;
        int val = q1.front();
        q1.pop();
        return val;
    }

    int top() {
        if (q1.empty()) return -1;
        return q1.front();
    }

    bool isEmpty() {
        return q1.empty();
    }

    int size() {
        return q1.size();
    }
};

// Please don't remove the code below
int main() {
    string input;
    getline(cin, input);
    
    // Parse input
    size_t pipePos = input.find('|');
    string operationsStr = input.substr(0, pipePos);
    string paramsStr = input.substr(pipePos + 1);
    
    // Parse operations
    vector<string> operations;
    size_t start = operationsStr.find('[');
    size_t end = operationsStr.find(']');
    
    if (start != string::npos && end != string::npos) {
        string opsContent = operationsStr.substr(start + 1, end - start - 1);
        size_t pos = 0;
        while ((pos = opsContent.find('"', pos)) != string::npos) {
            size_t endQuote = opsContent.find('"', pos + 1);
            if (endQuote != string::npos) {
                string op = opsContent.substr(pos + 1, endQuote - pos - 1);
                operations.push_back(op);
                pos = endQuote + 1;
            } else {
                break;
            }
        }
    }
    
    // Parse parameters
    vector<vector<int>> params;
    start = paramsStr.find('[');
    end = paramsStr.find_last_of(']');
    
    if (start != string::npos && end != string::npos) {
        string paramsContent = paramsStr.substr(start + 1, end - start - 1);
        size_t pos = 0;
        while ((pos = paramsContent.find('[', pos)) != string::npos) {
            size_t endBracket = paramsContent.find(']', pos);
            if (endBracket != string::npos) {
                string paramArrayStr = paramsContent.substr(pos + 1, endBracket - pos - 1);
                vector<int> paramArray;
                
                size_t commaPos = 0;
                size_t startPos = 0;
                while ((commaPos = paramArrayStr.find(',', startPos)) != string::npos) {
                    string numStr = paramArrayStr.substr(startPos, commaPos - startPos);
                    if (!numStr.empty()) {
                        paramArray.push_back(stoi(numStr));
                    }
                    startPos = commaPos + 1;
                }
                
                // Handle the last number
                if (startPos < paramArrayStr.length()) {
                    string numStr = paramArrayStr.substr(startPos);
                    if (!numStr.empty()) {
                        paramArray.push_back(stoi(numStr));
                    }
                }
                
                params.push_back(paramArray);
                pos = endBracket + 1;
            } else {
                break;
            }
        }
    }
    
    // Execute operations
    vector<string> results;
    StackUsingQueues stack;
    
    for (size_t i = 0; i < operations.size(); i++) {
        if (operations[i] == "push") {
            stack.push(params[i][0]);
            results.push_back("-1");
        } else if (operations[i] == "pop") {
            int result = stack.pop();
            results.push_back(to_string(result));
        } else if (operations[i] == "top") {
            int result = stack.top();
            results.push_back(to_string(result));
        } else if (operations[i] == "isEmpty") {
            bool result = stack.isEmpty();
            results.push_back(result ? "true" : "false");
        } else if (operations[i] == "size") {
            int result = stack.size();
            results.push_back(to_string(result));
        }
    }
    
    // Output results
    cout << "[";
    for (size_t i = 0; i < results.size(); i++) {
        if (results[i] == "null") {
            cout << "null";
        } else if (results[i] == "true" || results[i] == "false") {
            cout << results[i];
        } else {
            cout << results[i];
        }
        
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
`🔢 Stack` | `🔄 Queue` | `🛠️ Data Structures` | `💡 Simulated Data Structure`

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
