

# 🔐 DSA Sheet – Problem 2: 🔁 Reverse a Linked List  
**Day 14 – Coding Hero Sheet – C++**  

## 🎯 Problem Level  
**Medium**

---

## 🧩 Background  

Reversing a linked list in-place is a **fundamental problem** in data structures that evaluates your understanding of **pointers**, **linked list traversal**, and **manipulation**.  
It also lays the groundwork for more complex linked list operations like cycle detection, palindrome check, and merge operations.  

This problem helps sharpen skills in:  
- Traversal and update of node pointers  
- Understanding of list head/tail behavior  
- Iterative logic building  

---

## 📝 Problem Statement  

Implement a function that **reverses a singly linked list in-place** and returns the new head.  
You are given the head of the singly linked list. Do not use any additional data structures; reverse the list by manipulating node pointers.

> ✅ Each node in the list contains:  
> - `value`: the data  
> - `next`: pointer to the next node  

---

## 📥 Input Format  

- A string representing a **linked list array**, e.g., `[1, 2, 3, 4, 5]`.

---

## 📤 Output Format  

- A reversed linked list represented in the same array format, e.g., `[5, 4, 3, 2, 1]`.

---

## 🧪 Example  

### 🔹 Example 1  
```
Input:  [1, 2, 3, 4, 5]  
Output: [5, 4, 3, 2, 1]
```

### 🔹 Example 2  
```
Input:  [7, 14, 21]  
Output: [21, 14, 7]
```

---

## ⚙️ Constraints  
- `1 ≤ length of list ≤ 10^5`  
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
ListNode* reverseLinkedList(ListNode* head) {
    ListNode* prev = nullptr;
    ListNode* curr = head;
    
    while (curr) {
        ListNode* nextNode = curr->next;  // Store next node
        curr->next = prev;                // Reverse current node's pointer
        prev = curr;                      // Move prev to current
        curr = nextNode;                  // Move to next node
    }
    
    return prev; // New head
}

// Please don't remove the code below
int main() {
    string input;
    getline(cin, input);
    
    try {
        // Parse array
        vector<int> arr;
        size_t start = input.find('[');
        size_t end = input.find(']');
        
        if (start != string::npos && end != string::npos && start < end) {
            string content = input.substr(start + 1, end - start - 1);
            stringstream ss(content);
            string item;
            
            while (getline(ss, item, ',')) {
                if (!item.empty()) {
                    arr.push_back(stoi(item));
                }
            }
        }
        
        // Create linked list
        ListNode* head = nullptr;
        ListNode* current = nullptr;
        
        for (int val : arr) {
            if (!head) {
                head = new ListNode(val);
                current = head;
            } else {
                current->next = new ListNode(val);
                current = current->next;
            }
        }
        
        // Reverse the list
        ListNode* newHead = reverseLinkedList(head);
        
        // Convert back to array for verification
        vector<int> result;
        current = newHead;
        while (current) {
            result.push_back(current->value);
            current = current->next;
        }
        
        // Output result
        cout << "[";
        for (size_t i = 0; i < result.size(); i++) {
            cout << result[i];
            if (i < result.size() - 1) {
                cout << ",";
            }
        }
        cout << "]";
        
        // Clean up memory
        while (newHead) {
            ListNode* temp = newHead;
            newHead = newHead->next;
            delete temp;
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
`📚 Linked List` | `🔁 Reversal` | `🧠 Pointer Manipulation` | `💡 Iterative Approach`

---

## 👨‍💻 Author  

### 🚀 **Darshan Vasani**  
💡 **Full-Stack Developer | Software Engineer | Mentor**    

### 🔗 Connect with me! 🌍  
🌐 **Portfolio:** [dpvasani56.vercel.app](https://dpvasani56.vercel.app/)  
🐙 **GitHub:** [github.com/dpvasani](https://github.com/dpvasani)  
💼 **LinkedIn:** [linkedin.com/in/dpvasani56](https://www.linkedin.com/in/dpvasani56/)  
🌳 **Linktree:** [linktr.ee/dpvasani56](https://linktr.ee/dpvasani56)  
🎓 **Credly:** [credly.com/users/dpvasani55](https://www.credly.com/users/dpvasani55/)  
🐦 **Twitter:** [x.com/vasanidarshan56](https://x.com/vasanidarshan56)  
📢 **Topmate:** [topmate.io/dpvasani56](https://topmate.io/dpvasani56)  

---

🚀 **Follow me for more cool DSA problems & solutions!** 🌟

---