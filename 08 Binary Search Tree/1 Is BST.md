# 📌 DSA Sheet – 1 : ✅ Is BST  
## 🎯 Problem Level  
**Easy**

---

## 🧩 Background  

Hitesh loves **chai**, but his grandfather won't let him have any unless he solves a coding challenge.  
This time, the challenge is to determine whether a given binary tree is a **Binary Search Tree (BST)**.

A **Binary Search Tree (BST)** follows these rules:
- Left subtree contains only nodes with **keys less than** the node’s key.
- Right subtree contains only nodes with **keys greater than** the node’s key.
- Both left and right subtrees must also be BSTs.
- All nodes have **distinct keys**.

Help Hitesh earn his cup of chai ☕ by checking whether the given binary tree is a valid BST.

---

## 📝 Problem Statement  

You are given the root node of a binary tree.  
Determine whether it is a **valid Binary Search Tree (BST)**.  
Return `"YES"` if it is a BST, otherwise return `"NO"`.

---

## 📥 Input Format  
- First line: Integer `n` — number of nodes in the tree.  
- Second line: `n` integers representing the level-order traversal of the tree.  
  - Use `-1` for `NULL` (missing) child nodes.

---

## 📤 Output Format  
- Output `"YES"` if the tree is a valid BST, else `"NO"`.

---

## 🧪 Example  

### 🔹 Testcase  
```
Input:  
7  
10 5 15 -1 -1 12 20

Output:  
YES
```

**Explanation:**  
The tree structure is:  
```
      10
     /  \
    5   15
       /  \
     12    20
```
All left nodes < root, and all right nodes > root. So it’s a valid BST ✅.

---

## ⚙️ Constraints  
- Node values are in the range: `0 ≤ val ≤ 10⁹`
- Use `-1` to represent `NULL` children in level order.

---

## 💻 C++ Solution  

```cpp
#include <bits/stdc++.h>
using namespace std;

struct Node {
    int val;
    Node *left, *right;
    Node(int x) : val(x), left(NULL), right(NULL) {}
    Node() : val(0), left(NULL), right(NULL) {}
    Node(int x, Node* left, Node* right) : val(x), left(left), right(right) {}
};

// Helper function to check BST validity using range
bool isBSTUtil(Node* root, long long minVal, long long maxVal) {
    if (root == NULL) return true;

    if (root->val <= minVal || root->val >= maxVal) return false;

    return isBSTUtil(root->left, minVal, root->val) &&
           isBSTUtil(root->right, root->val, maxVal);
}

bool isBst(Node* root) {
    return isBSTUtil(root, LLONG_MIN, LLONG_MAX);
}

// Utility to build tree from level-order input
Node* getBinaryTree(vector<int>& arr){
    if (arr.empty()) return NULL;

    queue<Node*> qu;
    Node* root = new Node(arr[0]);
    qu.push(root);
    int idx = 1;

    while (idx < arr.size()) {
        auto curr = qu.front();
        qu.pop();

        if (arr[idx] == -1) curr->left = NULL;
        else {
            curr->left = new Node(arr[idx]);
            qu.push(curr->left);
        }
        idx++;

        if (idx < arr.size()) {
            if (arr[idx] == -1) curr->right = NULL;
            else {
                curr->right = new Node(arr[idx]);
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

    vector<int> nodeValues(n);
    for (int &x : nodeValues) {
        cin >> x;
    }

    Node* tree = getBinaryTree(nodeValues);

    if (isBst(tree)) {
        cout << "YES";
    } else {
        cout << "NO";
    }

    return 0;
}
```

---

## 🏷️ Tags  
`🌳 Binary Tree` | `✅ BST Validation` | `📚 Recursion` | `🧠 Invariants`

---

## 👨‍💻 Author  

### 🚀 **Darshan Vasani**  
💡 **Full-Stack Developer | Software Engineer | Mentor**  

### 🔗 Connect with me! 🌍  
🌐 **Portfolio:** [dpvasani56.vercel.app](https://dpvasani56.vercel.app)  
🐙 **GitHub:** [github.com/dpvasani](https://github.com/dpvasani)  
💼 **LinkedIn:** [linkedin.com/in/dpvasani56](https://www.linkedin.com/in/dpvasani56/)  
🌳 **Linktree:** [linktr.ee/dpvasani56](https://linktr.ee/dpvasani56)  
🎓 **Credly:** [credly.com/users/dpvasani55](https://www.credly.com/users/dpvasani55/)  
🐦 **Twitter:** [x.com/vasanidarshan56](https://x.com/vasanidarshan56)  
📢 **Topmate:** [topmate.io/dpvasani56](https://topmate.io/dpvasani56)

---

☕ Help Hitesh get his well-deserved chai — one tree at a time! 🌳