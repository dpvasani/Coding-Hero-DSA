# 📌 DSA Sheet – Problem 3: 🔗 Merge Two Sorted Linked Lists  
## 🎯 Problem Level  
**Medium**

---

## 🧩 Background  

Merging two sorted linked lists is a **fundamental problem** that demonstrates **pointer manipulation**, **recursive or iterative thinking**, and the importance of **in-place modifications** without creating new nodes. Mastering this helps in efficiently dealing with more advanced problems like merge sort for linked lists.

---

## 📝 Problem Statement  

Implement a function that merges **two sorted singly linked lists** into a single sorted linked list.

> ✅ Each input list node contains:
> - `value`: the integer data
> - `next`: pointer to the next node
>
> 🚨 Note:
> - The input linked lists are already sorted in ascending order.
> - The merged list must also be **sorted**.
> - The merge must be performed by **re-linking the nodes**, not by creating new ones.
> - Return the **head node** of the newly merged list.

---

## 📥 Input Format  

- A string input in the format:  
  `[list1 elements] | [list2 elements]`  
  Example: `[1, 3, 5] | [2, 4, 6]`

---

## 📤 Output Format  

- A string representing the merged sorted list in array format.  
  Example: `[1, 2, 3, 4, 5, 6]`

---

## 🧪 Example  

### 🔹 Example 1  
```
Input:  [1, 3, 5] | [2, 4, 6]  
Output: [1, 2, 3, 4, 5, 6]
```

### 🔹 Example 2  
```
Input:  [1, 2, 4] | [1, 3, 4]  
Output: [1, 1, 2, 3, 4, 4]
```

---

## ⚙️ Constraints  
- `0 ≤ length of each list ≤ 10^4`  
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
ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
    if (!list1) return list2;
    if (!list2) return list1;

    ListNode* head = nullptr;
    if (list1->value < list2->value) {
        head = list1;
        list1 = list1->next;
    } else {
        head = list2;
        list2 = list2->next;
    }

    ListNode* current = head;
    while (list1 && list2) {
        if (list1->value < list2->value) {
            current->next = list1;
            list1 = list1->next;
        } else {
            current->next = list2;
            list2 = list2->next;
        }
        current = current->next;
    }

    current->next = list1 ? list1 : list2;
    return head;
}

// Helper function to create a linked list from vector
ListNode* createList(const vector<int>& arr) {
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
    return head;
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

        string arr1Str = input.substr(0, pipePos);
        string arr2Str = input.substr(pipePos + 1);

        vector<int> arr1, arr2;

        size_t start1 = arr1Str.find('['), end1 = arr1Str.find(']');
        if (start1 != string::npos && end1 != string::npos && start1 < end1) {
            stringstream ss(arr1Str.substr(start1 + 1, end1 - start1 - 1));
            string item;
            while (getline(ss, item, ',')) {
                if (!item.empty()) arr1.push_back(stoi(item));
            }
        }

        size_t start2 = arr2Str.find('['), end2 = arr2Str.find(']');
        if (start2 != string::npos && end2 != string::npos && start2 < end2) {
            stringstream ss(arr2Str.substr(start2 + 1, end2 - start2 - 1));
            string item;
            while (getline(ss, item, ',')) {
                if (!item.empty()) arr2.push_back(stoi(item));
            }
        }

        ListNode* list1 = createList(arr1);
        ListNode* list2 = createList(arr2);

        ListNode* mergedHead = mergeTwoLists(list1, list2);

        vector<int> result;
        ListNode* current = mergedHead;
        while (current) {
            result.push_back(current->value);
            current = current->next;
        }

        cout << "[";
        for (size_t i = 0; i < result.size(); i++) {
            cout << result[i];
            if (i < result.size() - 1) cout << ",";
        }
        cout << "]";

        while (mergedHead) {
            ListNode* temp = mergedHead;
            mergedHead = mergedHead->next;
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
`📚 Linked List` | `🔁 Iteration / Recursion` | `🧠 In-Place Merge` | `🛠️ Two Pointers`

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