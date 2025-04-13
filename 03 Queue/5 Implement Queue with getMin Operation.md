# 🧩 DSA Sheet – Problem 5: Implement Queue with getMin Operation

## 🎯 Problem Level  
**Medium**

---

## 📚 Problem Background  

In this problem, you need to implement a queue with a special operation, `getMin()`, that returns the minimum element of the queue in constant time (O(1)). The operations on the queue should include the standard enqueue, dequeue, peek, and a getMin operation, which should work efficiently in O(1) time.

---

## 📝 Problem Statement  

You need to implement a queue that supports the following operations:
- **enqueue(element)**: Adds an element to the rear of the queue.
- **dequeue()**: Removes and returns the front element of the queue.
- **peek()**: Returns the front element without removing it.
- **getMin()**: Returns the minimum element in the queue in **O(1)** time.
- **isEmpty()**: Checks if the queue is empty.

For example:
- **Input**: `["MinQueue", "enqueue", "enqueue", "enqueue", "getMin", "dequeue", "getMin", "peek"]`
- **Parameters**: `[[], [11], [51], [1], [], [], [], []]`
- **Output**: `[null, null, null, null, 1, 3, 1, 1]`

---

## 📥 Input Format  

- The input contains a list of operations on the queue in the form of strings and corresponding parameters.
  
---

## 📤 Output Format  

- For each operation, output the result:
  - For `enqueue` and `dequeue`, the result is `null`.
  - For `getMin`, `peek`, `isEmpty`, and `size`, return the respective result.
  
---

## 🧪 Example  

### 🔹 Example 1  

**Input**  
```
["MinQueue", "enqueue", "enqueue", "enqueue", "getMin", "dequeue", "getMin", "peek"]
[[], [11], [51], [1], [], [], [], []]
```

**Output**  
```
[null, null, null, null, 1, 3, 1, 1]
```

**Explanation**  
- `enqueue(11)` adds 11 to the queue.
- `enqueue(51)` adds 51 to the queue.
- `enqueue(1)` adds 1 to the queue.
- `getMin()` returns 1, which is the smallest element in the queue.
- `dequeue()` removes 11 from the queue.
- `getMin()` returns 1 again since it is still the smallest element.
- `peek()` returns 1, which is now at the front of the queue.

---

## ⚙️ Constraints  

- The queue will always support these operations.
- The `getMin()` operation must be implemented efficiently in **O(1)** time.

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <queue>
#include <vector>
#include <string>
using namespace std;

// MinQueue class implementation
class MinQueue {
private:
    queue<int> q;  // main queue
    queue<int> minQueue;  // queue to track the minimum elements
    
public:
    MinQueue() {
        // constructor, no need for initialization
    }
    
    void enqueue(int x) {
        q.push(x);
        
        // Maintain the minQueue invariant: front of minQueue is the smallest element
        while (!minQueue.empty() && minQueue.back() > x) {
            minQueue.pop();
        }
        minQueue.push(x);
    }
    
    int dequeue() {
        if (q.empty()) return -1;  // Assuming -1 for empty queue (or error handling)
        
        int front = q.front();
        q.pop();
        
        // If the element to dequeue is the same as the front of minQueue, pop from minQueue too
        if (front == minQueue.front()) {
            minQueue.pop();
        }
        
        return front;
    }
    
    int peek() {
        if (q.empty()) return -1;  // Assuming -1 for empty queue (or error handling)
        return q.front();
    }
    
    int getMin() {
        if (minQueue.empty()) return -1;  // Assuming -1 for empty queue (or error handling)
        return minQueue.front();
    }
    
    bool isEmpty() {
        return q.empty();
    }
    
    int size() {
        return q.size();
    }
};

// Please don't remove the code below
int main() {
    string input;
    getline(cin, input);
    
    try {
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
                    
                    if (!paramArrayStr.empty()) {
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
        MinQueue* minQueue = nullptr;
        
        for (size_t i = 0; i < operations.size(); i++) {
            if (operations[i] == "MinQueue") {
                minQueue = new MinQueue();
                results.push_back("null");
            } else if (operations[i] == "enqueue") {
                minQueue->enqueue(params[i][0]);
                results.push_back("null");
            } else if (operations[i] == "dequeue") {
                int result = minQueue->dequeue();
                results.push_back(to_string(result));
            } else if (operations[i] == "peek") {
                int result = minQueue->peek();
                results.push_back(to_string(result));
            } else if (operations[i] == "getMin") {
                int result = minQueue->getMin();
                results.push_back(to_string(result));
            } else if (operations[i] == "isEmpty") {
                bool result = minQueue->isEmpty();
                results.push_back(result ? "true" : "false");
            } else if (operations[i] == "size") {
                int result = minQueue->size();
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
        
        // Clean up
        delete minQueue;
    } catch (const exception&) {
        cout << "Invalid input";
    }
    
    return 0;
}
```

---

## 🏷️ Tags  
`🔢 Queue` | `🔍 Min` | `🛠️ Data Structure` | `💡 Efficient Operations`

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
