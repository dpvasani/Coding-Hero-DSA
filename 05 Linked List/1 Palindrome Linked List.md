# 🔐 DSA Sheet – Problem 3: 🔁 Palindrome Linked List  
## 🎯 Problem Level  
**Easy**

---

## 🧩 Background  

Checking if a linked list is a **palindrome** is a classic problem that tests your understanding of **pointer manipulation**, **linked list traversal**, and **in-place reversal**. Instead of converting the list into an array (which uses O(n) space), this problem emphasizes an **efficient in-place** approach using the **two-pointer technique** and **reversing half of the list**.

---

## 📝 Problem Statement  

Implement a function that determines whether a singly linked list is a **palindrome** (reads the same forward and backward).

You are given the head of the singly linked list. Your function should return `true` if the list is a palindrome and `false` otherwise.

> ✅ Each node in the list contains:
> - `value`: the data
> - `next`: pointer to the next node

---

## 📥 Input Format  

- A string representing a **linked list array**, e.g., `[1, 2, 2, 1]`.

---

## 📤 Output Format  

- Output `true` or `false` (as a string) depending on whether the list is a palindrome.

---

## 🧪 Example  

### 🔹 Example 1  
```
Input:  [1, 2, 2, 1]
Output: true
```

### 🔹 Example 2  
```
Input:  [1, 2, 3]
Output: false
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

bool isPalindrome(ListNode* head) {
    if (!head || !head->next) return true;

    // Step 1: Find the middle using slow and fast pointers
    ListNode* slow = head;
    ListNode* fast = head;
    
    while (fast && fast->next) {
        slow = slow->next;
        fast = fast->next->next;
    }

    // Step 2: Reverse the second half of the list
    ListNode* prev = nullptr;
    ListNode* curr = slow;
    while (curr) {
        ListNode* nextTemp = curr->next;
        curr->next = prev;
        prev = curr;
        curr = nextTemp;
    }

    // Step 3: Compare first and second halves
    ListNode* firstHalf = head;
    ListNode* secondHalf = prev;
    while (secondHalf) {
        if (firstHalf->value != secondHalf->value)
            return false;
        firstHalf = firstHalf->next;
        secondHalf = secondHalf->next;
    }

    return true;
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
        
        // Check if palindrome
        bool result = isPalindrome(head);
        
        // Output result
        cout << (result ? "true" : "false");
        
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
`📚 Linked List` | `🎯 Two Pointers` | `🔄 In-Place Reversal` | `🧠 Palindrome Logic`

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
