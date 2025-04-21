# 📌 DSA Sheet – 2 : ✅ Search in BST  
## 🎯 Problem Level  
**Easy**

---

## 🧩 Background  

Hitesh and Anirudh are in serious trouble! Their best friend **Akash** has been arrested for allegedly hitting a policeman.  

They know Akash is innocent and decide to find him in the **jail**, which is organized like a **Binary Search Tree (BST)**.  
Luckily, Hitesh knows Akash's **cell ID**, and Anirudh has access to the entire jail structure.

Each **cell** is a node with:
- A unique **cell ID**
- A **prisoner’s name**

The jail follows BST rules:
- Left cell ID < current cell ID  
- Right cell ID > current cell ID  

Time is ticking! Help Hitesh and Anirudh locate Akash.

---

## 📝 Problem Statement  

You are given the root node of a jail (BST) and a **target cell ID**.  

Your task is to implement a function that returns:  
- `"Help!!!"` if the cell with that ID exists and **Akash** is in it  
- `"Hurrah!!!"` if the cell with that ID exists but **Akash is not there**  
- `"Wrong Jail"` if the cell ID **doesn’t exist** in the BST

You must solve this in **O(log n)** time.

---

## 📥 Input Format  
- First line: Integer `n` — number of nodes in the jail tree  
- Next `n` lines: Each line has an integer `cellID` and a string `prisonerName`  
- Final line: Integer `cellId` to search

Use `-1` for null pointers (when constructing the tree in level order)

---

## 📤 Output Format  
Print one of the following strings:  
- `"Help!!!"`  
- `"Hurrah!!!"`  
- `"Wrong Jail"`

---

## 🧪 Example  

### 🔹 Testcase  
```
Input:  
7  
1000 Priyo  
500 Ayan  
1500 Akash  
-1 -  
-1 -  
-1 -  
-1 -  
1500

Output:  
Help!!!
```

**Explanation:**  
BST Structure:
```
       1000 (Priyo)
      /           \
  500 (Ayan)     1500 (Akash)
```
We found cell ID `1500`, and Akash is in it ✅

---

## ⚙️ Constraints  
- `1 ≤ n ≤ 10⁵`  
- `1 ≤ cellID ≤ 10⁹`  
- `1 ≤ length(prisonerName) ≤ 20`  
- Names can repeat; cell IDs are unique  
- Tree is a **valid BST**

---

## 💻 C++ Solution  

```cpp
#include <bits/stdc++.h>
using namespace std;

struct Node {
    int ID; // Cell ID
    string name; // Prisoner Name
    Node *left, *right;
    Node(int id, string name) : ID(id), name(name), left(NULL), right(NULL) {}
    Node() : ID(-1), name(""), left(NULL), right(NULL) {}
    Node(int id, string name, Node* left, Node* right) : ID(id), name(name), left(left), right(right) {}
};

string check(Node* root, int cellId) {
    while (root != NULL) {
        if (cellId == root->ID) {
            if (root->name == "Akash") {
                return "Help!!!";
            } else {
                return "Hurrah!!!";
            }
        } else if (cellId < root->ID) {
            root = root->left;
        } else {
            root = root->right;
        }
    }
    return "Wrong Jail";
}

// Building the tree
Node* getBinaryTree(vector<pair<int, string>>& arr) {
    if (arr.empty()) return nullptr;
    queue<Node*> qu;
    Node* root = new Node(arr[0].first, arr[0].second);
    qu.push(root);
    int idx = 1;
    while (idx < arr.size()) {
        auto curr = qu.front(); qu.pop();
        if (arr[idx].first == -1) {
            curr->left = NULL;
        } else {
            curr->left = new Node(arr[idx].first, arr[idx].second);
            qu.push(curr->left);
        }
        idx++;
        if (idx < arr.size()) {
            if (arr[idx].first == -1) {
                curr->right = NULL;
            } else {
                curr->right = new Node(arr[idx].first, arr[idx].second);
                qu.push(curr->right);
            }
            idx++;
        }
    }
    return root;
}

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(0); cout.tie(0);
    int n;
    cin >> n;
    vector<pair<int, string>> nodeValues(n);
    for (int i = 0; i < n; i++) {
        cin >> nodeValues[i].first >> nodeValues[i].second;
    }
    int cellId;
    cin >> cellId;
    Node* root = getBinaryTree(nodeValues);
    cout << check(root, cellId);
    return 0;
}
```

---

## 🏷️ Tags  
`🌳 Binary Search Tree` | `🔍 Search` | `🧠 Logic` | `📚 BST Traversal`

---

## 👨‍💻 Author  

### 🚀 **Darshan Vasani**  
💡 **Full-Stack Developer | Software Engineer | Mentor**  

### 🔗 Connect with me! 🌍  
🌐 **Portfolio:** [dpvasani56.vercel.app](https://dpvasani56.vercel.app)  
🐙 **GitHub:** [github.com/dpvasani](https://github.com/dpvasani)  
💼 **LinkedIn:** [linkedin.com/in/dpvasani56](https://www.linkedin.com/in/dpvasani56/)  
🌳 **Linktree:** [linktr.ee/dpvasani56](https://linktr.ee/dpvasani56)  
🎓 **Credly:** [credly.com/users/dpvasani57](https://www.credly.com/users/dpvasani57/)  
🐦 **Twitter:** [x.com/vasanidarshan56](https://x.com/vasanidarshan56)  
📢 **Topmate:** [topmate.io/dpvasani56](https://topmate.io/dpvasani56)

---

☕ Help Akash break out—or prove his innocence—the BST way! 🕵️‍♂️🌲

---