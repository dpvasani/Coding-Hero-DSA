# 🧩 DSA Sheet – Problem 2: Generate Binary Numbers

## 🎯 Problem Level  
**Medium**

---

## 📚 Problem Background  

This problem tests your understanding of using a queue to generate binary numbers efficiently. A queue is a First In, First Out (FIFO) data structure, which we can utilize to generate binary numbers from 1 to n. Instead of converting each number to binary individually, we can build the binary numbers sequentially by using the queue operations.

--- 

## 📝 Problem Statement  

Given:
- An integer `n`, the task is to generate the binary representation of all numbers from 1 to `n`.
- You must use a queue to generate these numbers.
- The queue is implemented with these operations:
    - `enqueue`: Add an element at the end using `push()`.
    - `dequeue`: Remove an element from the front using `shift()`.
    - `isEmpty`: Check if the queue is empty by checking the length.

You need to implement a function `generateBinaryNumbers(n)` that returns a list of binary numbers from 1 to n, generated using a queue.

---

## 📥 Input Format  

- A single integer `n` (1 ≤ n ≤ 1000) that represents the range of numbers to generate the binary representations for.

---

## 📤 Output Format  

- A list of strings containing the binary representations of numbers from 1 to n.

---

## 🧪 Example  

### 🔹 Example 1  

**Input**  
```
3
```

**Output**  
```
["1", "10", "11"]
```

**Explanation**  
- Binary representations from 1 to 3 are: "1", "10", "11".

---

## ⚙️ Constraints  

- 1 ≤ n ≤ 1000  

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <iostream>
#include <vector>
#include <string>
#include <queue>
using namespace std;

// Function to generate binary numbers from 1 to n using a queue
vector<string> generateBinaryNumbers(int n) {
    vector<string> result;
    if (n <= 0) return result; // Return an empty list for non-positive n

    queue<string> q;
    
    // Enqueue the first binary number '1'
    q.push("1");

    for (int i = 0; i < n; i++) {
        // Dequeue the front element
        string curr = q.front();
        q.pop();
        
        // Add the current binary number to the result
        result.push_back(curr);
        
        // Generate the next binary numbers by appending '0' and '1'
        q.push(curr + "0");
        q.push(curr + "1");
    }
    
    return result;
}

// Please don't remove the code below
int main() {
    string input;
    getline(cin, input);
    
    try {
        int n = stoi(input);
        if (n < 0) {
            cout << "Invalid input";
            return 0;
        }
        
        vector<string> result = generateBinaryNumbers(n);
        
        // Output the result
        cout << "[";
        for (size_t i = 0; i < result.size(); i++) {
            cout << "\"" << result[i] << "\"";
            if (i < result.size() - 1) {
                cout << ",";
            }
        }
        cout << "]";
    } catch (const exception& e) {
        cout << "Invalid input";
    }
    
    return 0;
}
```

---

## 🏷️ Tags  
`🔢 Binary Numbers` | `🛠️ Queue` | `💡 Sequence Generation` | `🎨 Data Structures`

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