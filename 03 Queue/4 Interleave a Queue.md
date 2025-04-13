# 🧩 DSA Sheet – Problem 4: Interleave a Queue

## 🎯 Problem Level  
**Medium**

---

## 📚 Problem Background  

In this problem, you are given a queue of an even number of elements, and your task is to interleave the first half of the queue with the second half. The operations on the queue are standard (enqueue, dequeue, and checking if the queue is empty), but this problem tests your ability to manipulate a queue by splitting it into two halves and merging them in an interleaved manner.

---

## 📝 Problem Statement  

Given a queue of integers with an even number of elements, your task is to interleave the first half with the second half.

For example:
- **Input**: `[1, 2, 3, 4, 5, 6]`
- **Output**: `[1, 4, 2, 5, 3, 6]`

- **Input**: `[11, 12, 13, 14]`
- **Output**: `[11, 13, 12, 14]`

The queue supports the following operations:
- `enqueue`: Add an element at the end using `push()`.
- `dequeue`: Remove an element from the front using `shift()`.
- `isEmpty`: Check if the queue is empty by checking the length.

---

## 📥 Input Format  

- A queue of integers implemented as an array with an even number of elements (e.g., `[1, 2, 3, 4]`).

---

## 📤 Output Format  

- A new array where the first half of the elements is interleaved with the second half.

---

## 🧪 Example  

### 🔹 Example 1  

**Input**  
```
[1, 2, 3, 4]
```

**Output**  
```
[1, 3, 2, 4]
```

**Explanation**  
- The first half `[1, 2]` and the second half `[3, 4]` are interleaved to form `[1, 3, 2, 4]`.

---

## ⚙️ Constraints  

- The queue will always contain an even number of elements.

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <vector>
#include <queue>
#include <string>
using namespace std;

// Function to interleave the first half with the second half
vector<int> interleaveQueue(queue<int> q) {
    // First, get the size of the queue
    int n = q.size();
    // Create a temporary queue to store the first half of the elements
    queue<int> tempQueue;

    // Dequeue the first half and store in tempQueue
    for (int i = 0; i < n / 2; ++i) {
        tempQueue.push(q.front());
        q.pop();
    }
    
    // Now, interleave the elements of tempQueue with the second half of q
    vector<int> result;
    while (!tempQueue.empty()) {
        // Add one element from the first half (tempQueue)
        result.push_back(tempQueue.front());
        tempQueue.pop();
        
        // Add one element from the second half (original queue q)
        result.push_back(q.front());
        q.pop();
    }

    return result;
}

// Please don't remove the code below
int main() {
    string input;
    getline(cin, input);
    
    try {
        // Parse the input array to create a queue
        queue<int> q;
        size_t start = input.find('[');
        size_t end = input.find(']');
        
        if (start != string::npos && end != string::npos) {
            string queueContent = input.substr(start + 1, end - start - 1);
            size_t pos = 0;
            size_t commaPos;
            
            while ((commaPos = queueContent.find(',', pos)) != string::npos) {
                string numStr = queueContent.substr(pos, commaPos - pos);
                if (!numStr.empty()) {
                    q.push(stoi(numStr));
                }
                pos = commaPos + 1;
            }
            
            // Handle the last number
            if (pos < queueContent.length()) {
                string numStr = queueContent.substr(pos);
                if (!numStr.empty()) {
                    q.push(stoi(numStr));
                }
            }
        }
        
        // Get the result
        vector<int> result = interleaveQueue(q);
        
        // Output the result
        cout << "[";
        for (size_t i = 0; i < result.size(); i++) {
            cout << result[i];
            if (i < result.size() - 1) {
                cout << ",";
            }
        }
        cout << "]";
    }
    catch (const exception&) {
        cout << "Invalid input";
    }
    
    return 0;
}
```

---

## 🏷️ Tags  
`🔢 Queue` | `🔀 Interleave` | `🛠️ Data Structure Manipulation` | `💡 Queue Manipulation`

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
