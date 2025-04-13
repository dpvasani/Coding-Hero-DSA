# 🧩 DSA Sheet – Problem 5: Rotate a Queue K Times

## 🎯 Problem Level  
**Easy**

---

## 📚 Problem Background  

In this problem, you are given a queue of integers and a number `k`. Your task is to rotate the queue `k` times, meaning the front element of the queue should be moved to the rear `k` times. The operations you can perform on the queue include enqueue, dequeue, and checking if the queue is empty. This problem tests your ability to manipulate a queue and perform rotation operations efficiently.

---

## 📝 Problem Statement  

You are given a queue of integers and a number `k`. Your task is to rotate the queue `k` times, meaning the front element should be moved to the rear `k` times.

For example:

- **Input**: `[1, 2, 3, 4, 5]` and `k = 2`
- **Output**: `[3, 4, 5, 1, 2]`

- **Input**: `[10, 20, 30, 40, 50]` and `k = 3`
- **Output**: `[40, 50, 10, 20, 30]`

The queue supports the following operations:
- `enqueue`: Add an element at the end using `push()`.
- `dequeue`: Remove an element from the front using `shift()`.
- `isEmpty`: Check if the queue is empty by checking the `length`.

---

## 📥 Input Format  

- A queue of integers represented as an array (e.g., `[1, 2, 3, 4, 5]`).
- A number `k`, representing the number of rotations.

---

## 📤 Output Format  

- A new array, which is the rotated queue after performing `k` rotations.

---

## 🧪 Example  

### 🔹 Example 1  

**Input**  
```
[1, 2, 3, 4, 5], 2
```

**Output**  
```
[3, 4, 5, 1, 2]
```

**Explanation**  
- The first two elements `[1, 2]` are moved to the end, resulting in `[3, 4, 5, 1, 2]`.

---

## ⚙️ Constraints  

- The queue will always contain an even number of elements.
- `k` will be less than or equal to the size of the queue.

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <vector>
#include <queue>
#include <string>
using namespace std;

// Function to rotate the queue k times
vector<int> rotateQueue(queue<int> q, int k) {
    // Get the size of the queue
    int size = q.size();
    
    // Ensure k is within the range of the queue's size
    k = k % size;
    
    // Rotate the queue k times
    for (int i = 0; i < k; i++) {
        // Remove the front element and push it to the back
        int frontElement = q.front();
        q.pop();
        q.push(frontElement);
    }
    
    // Convert the queue to a vector for output
    vector<int> result;
    while (!q.empty()) {
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
        size_t pipePos = input.find('|');
        if (pipePos == string::npos) {
            cout << "Invalid input";
            return 0;
        }
        
        string queueStr = input.substr(0, pipePos);
        string kStr = input.substr(pipePos + 1);
        
        // Parse the queue
        queue<int> q;
        size_t start = queueStr.find('[');
        size_t end = queueStr.find(']');
        
        if (start != string::npos && end != string::npos) {
            string queueContent = queueStr.substr(start + 1, end - start - 1);
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
        
        // Parse k
        int k = stoi(kStr);
        
        // Get the result
        vector<int> result = rotateQueue(q, k);
        
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
`🔢 Queue` | `🔄 Rotation` | `🛠️ Data Structure Manipulation` | `💡 Queue Manipulation`

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