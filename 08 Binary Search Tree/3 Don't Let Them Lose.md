# 📌 DSA Sheet – 3 : ✅ Don't Let Them Lose  
## 🎯 Problem Level  
**Medium**

---

## 🧩 Background  

Anirudh and Hitesh are participating in a coding contest organized by Akash, the problem setter famous for tricky questions.  
This time, Akash gave them a unique challenge that could decide whether they win or lose.

They’re given a **Binary Search Tree (BST)**, and their task is to convert it into a **Greater Sum Tree (GST)**.

> In a GST, each node's new value is the **sum of all original node values greater than or equal to it**.

Help them win the contest and earn their glory! 🏆

---

## 📝 Problem Statement  

You are given the root of a Binary Search Tree (BST).  
Convert it into a **Greater Sum Tree (GST)**, where each node’s value becomes:

```
new_val = original_val + sum(all nodes with value > original_val)
```

You need to implement a function `convertBstToGst(Node* root)` which modifies the BST in-place.

---

## 📥 Input Format  
- First line: Integer `n` — number of nodes in the tree.  
- Second line: `n` integers representing the level-order traversal of the BST.  
  - Use `-1` to represent `NULL` (missing) child nodes.

---

## 📤 Output Format  
- Output `"YES"` if the BST is correctly converted to a Greater Sum Tree, else output `"NO"`.

---

## 🧪 Example  

### 🔹 Testcase  
```
Input:  
15  
4 1 6 0 2 5 7 -1 -1 -1 3 -1 -1 -1 8

Output:  
YES
```

**Explanation:**  
The original BST and GST are compared node-by-node. If transformation is correct, output is `"YES"`.

---

## ⚙️ Constraints  
- `1 ≤ n ≤ 100`  
- `0 ≤ Node.val ≤ 10⁹`  
- All node values are **unique**

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

// Convert BST to GST (main logic)
void helper(Node* root, int &sum) {
    if (!root) return;
    helper(root->right, sum);
    root->val += sum;
    sum = root->val;
    helper(root->left, sum);
}

void convertBstToGst(Node* root) {
    int sum = 0;
    helper(root, sum);
}

// Utility to build original and copy trees for comparison
pair<Node*,Node*> getBinaryTree(vector<int>& arr){
    if(arr.size() == 0) return {NULL, NULL};
    pair<Node*, Node*> ans;
    queue<Node*> qu;
    
    Node* root = new Node(arr[0]);
    qu.push(root);
    ans.first = root;
    
    int idx = 1;
    while(idx < arr.size()){
        auto curr = qu.front(); qu.pop();
        if(arr[idx] == -1) curr->left = NULL;
        else { curr->left = new Node(arr[idx]); qu.push(curr->left); }
        idx++;
        if(arr[idx] == -1) curr->right = NULL;
        else { curr->right = new Node(arr[idx]); qu.push(curr->right); }
        idx++;
    }

    while(!qu.empty()) qu.pop();
    
    root = new Node(arr[0]);
    qu.push(root);
    idx = 1;
    ans.second = root;
    
    while(idx < arr.size()){
        auto curr = qu.front(); qu.pop();
        if(arr[idx] == -1) curr->left = NULL;
        else { curr->left = new Node(arr[idx]); qu.push(curr->left); }
        idx++;
        if(arr[idx] == -1) curr->right = NULL;
        else { curr->right = new Node(arr[idx]); qu.push(curr->right); }
        idx++;
    }
    
    return ans;
}

// Function to transform 2nd tree for checking correctness
void f(Node* root, int &sum){
    if(root == NULL) return;
    f(root->right, sum);
    root->val += sum;
    sum = root->val;
    f(root->left, sum);
}

// Compare two trees
bool isSame(Node* root1, Node* root2){
    if(!root1 && !root2) return true;
    if(!root1 || !root2) return false;
    if(root1->val != root2->val) return false;
    return isSame(root1->left, root2->left) && isSame(root1->right, root2->right);
}

int main(){
    ios_base::sync_with_stdio(false);
    cin.tie(0); cout.tie(0);

    int n;
    cin >> n;
    vector<int> nodeValues(n);
    for(int &x : nodeValues) cin >> x;
    
    auto trees = getBinaryTree(nodeValues);
    
    convertBstToGst(trees.first);
    
    int sum = 0;
    f(trees.second, sum);
    
    if(isSame(trees.first, trees.second)){
        cout << "YES";
    } else {
        cout << "NO";
    }
    return 0;
}
```

---

## 🏷️ Tags  
`🌳 Binary Tree` | `🎯 Greater Sum Tree` | `🧠 Reverse Inorder` | `📚 Recursion`

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

☕ Help Anirudh & Hitesh win with GST – Greater Sum Tree, not Goods & Services Tax! 😄