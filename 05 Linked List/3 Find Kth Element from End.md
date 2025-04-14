# 📌 DSA Sheet – Problem 14: 🔢 Find Kth Element from End  
## 🎯 Problem Level  
**Medium**

---

## 🧩 Background  

Finding the **kth element from the end** of a singly linked list is a classic problem that teaches **pointer manipulation**, **fast-slow pointer technique**, and performing operations in a **single pass** to ensure O(n) time and O(1) space complexity. This efficient approach helps in solving problems where you cannot afford to traverse the list twice or use additional memory.

---

## 📝 Problem Statement  

Implement a function that returns the **kth node from the end** of a singly linked list. If `k` is greater than the number of nodes in the list, return `-1`.

> ✅ Each node in the list contains:
> - `value`: the data
> - `next`: pointer to the next node

---

## 📥 Input Format  

- A string in the format: `[linked list elements] | k`  
  Example: `[1, 2, 3, 4, 5] | 2`

---

## 📤 Output Format  

- Output the value of the `kth` node from the end.  
- Output `-1` if `k` exceeds the length of the list.

---

## 🧪 Example  

### 🔹 Example 1  
```
Input:  [1, 2, 3, 4, 5] | 2  
Output: 4
```

### 🔹 Example 2  
```
Input:  [10, 20, 30] | 5  
Output: -1
```

---

## ⚙️ Constraints  
- `1 ≤ length of list ≤ 10^5`  
- `1 ≤ k ≤ 10^5`  
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
int findKthFromEnd(ListNode* head, int k) {
    if (!head || k <= 0) return -1;

    ListNode* first = head;
    ListNode* second = head;

    // Move 'first' pointer k steps ahead
    for (int i = 0; i < k; ++i) {
        if (!first) return -1;  // k is larger than the length
        first = first->next;
    }

    // Move both pointers until 'first' reaches the end
    while (first) {
        first = first->next;
        second = second->next;
    }

    return second ? second->value : -1;
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
        string kStr = input.substr(pipePos + 1);
        
        // Parse k
        int k = stoi(kStr);
        
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
        
        // Get result
        int result = findKthFromEnd(head, k);
        
        // Output result
        cout << result;
        
        // Clean up memory
        while (head) {
            ListNode* temp = head;
            head = head->next;
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
`📚 Linked List` | `🎯 Two Pointers` | `🧠 Kth Element Logic` | `🚀 One-Pass Algorithm`

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