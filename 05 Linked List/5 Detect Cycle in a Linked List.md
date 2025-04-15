# 📌 DSA Sheet – Problem 4: 🔁 Detect Cycle in a Linked List  

## 🎯 Problem Level  
**Medium**

---

## 🧩 Background  

Detecting a **cycle in a linked list** is a key problem in the study of data structures, especially in real-world applications like cache implementations, navigation systems, or detecting infinite loops in graphs. The most efficient technique is **Floyd’s Cycle Detection Algorithm**, which uses **two pointers** (slow and fast) moving at different speeds. If there’s a cycle, these pointers will eventually meet.

---

## 📝 Problem Statement  

Implement a function that returns `true` if a singly linked list contains a **cycle**, otherwise `false`.  

A **cycle** occurs when a node’s `next` pointer points to a previously visited node.

> ✅ Each node in the list contains:
> - `value`: the data  
> - `next`: pointer to the next node  

---

## 📥 Input Format  

- A string in the format: `[linked list elements] | cycle position`  
  - Example: `[1, 2, 3, 4, 5] | 1`  
  - Here, the node with value 5 connects back to the node at index 1 (0-indexed).

---

## 📤 Output Format  

- Output `"true"` if a cycle exists in the linked list.  
- Output `"false"` if no cycle exists.

---

## 🧪 Example  

### 🔹 Example 1  
```
Input:  [1, 2, 3, 4, 5] | 1  
Output: true
```

### 🔹 Example 2  
```
Input:  [1, 2, 3] | -1  
Output: false
```

---

## ⚙️ Constraints  
- `1 ≤ length of list ≤ 10^5`  
- `-1 ≤ cycle position < length of list`  
- `-10^5 ≤ Node value ≤ 10^5`  

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <vector>
#include <string>
#include <sstream>
using namespace std;

// Definition for singly-linked list
struct ListNode {
    int value;
    ListNode *next;
    ListNode(int x) : value(x), next(nullptr) {}
};

// Please implement this function only
bool detectCycle(ListNode* head) {
    if (!head) return false;

    ListNode* slow = head;
    ListNode* fast = head;

    while (fast && fast->next) {
        slow = slow->next;
        fast = fast->next->next;

        if (slow == fast)
            return true;
    }

    return false;
}

// Please don't remove the code below
int main() {
    string input;
    getline(cin, input);
    
    try {
        // Parse input
        size_t pipePos = input.find('|');
        if (pipePos == string::npos) {
            cout << "Invalid input";
            return 0;
        }
        
        string arrStr = input.substr(0, pipePos);
        string cyclePos = input.substr(pipePos + 1);
        
        // Parse array
        vector<int> arr;
        size_t start = arrStr.find('[');
        size_t end = arrStr.find(']');
        
        if (start != string::npos && end != string::npos && start < end) {
            string content = arrStr.substr(start + 1, end - start - 1);
            stringstream ss(content);
            string item;
            
            while (getline(ss, item, ',')) {
                if (!item.empty()) {
                    arr.push_back(stoi(item));
                }
            }
        }
        
        int pos = stoi(cyclePos);
        
        // Create linked list
        ListNode* head = nullptr;
        ListNode* current = nullptr;
        vector<ListNode*> nodes;
        
        for (int val : arr) {
            if (!head) {
                head = new ListNode(val);
                current = head;
            } else {
                current->next = new ListNode(val);
                current = current->next;
            }
            nodes.push_back(current);
        }
        
        // Create cycle if needed
        if (pos >= 0 && pos < arr.size()) {
            current->next = nodes[pos];
        }
        
        // Detect cycle
        bool result = detectCycle(head);
        
        // Output result
        cout << (result ? "true" : "false");
        
        // Clean up memory (careful with cycles)
        if (pos < 0 || pos >= arr.size()) {
            while (head) {
                ListNode* temp = head;
                head = head->next;
                delete temp;
            }
        } else {
            // Break the cycle before cleanup
            if (current) current->next = nullptr;
            while (head) {
                ListNode* temp = head;
                head = head->next;
                delete temp;
            }
        }
    }
    catch (const exception&) {
        cout << "Invalid input";
    }
    
    return 0;
}
```

---

## 🏷️ Tags  
`📚 Linked List` | `🔁 Cycle Detection` | `🐢🐇 Floyd’s Algorithm` | `🔎 Two Pointers`

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

🔥 **Stay tuned for more handpicked DSA problems and efficient solutions!** 💡

---