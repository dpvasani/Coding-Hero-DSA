# 📌 DSA Sheet – 3 : ✅ Akash's Wedding Gift
## 🎯 Problem Level  
**Medium**  

---

## 🧩 Background  

Hitesh and Anirudh, two best friends, have been invited to their friend Akash's wedding. They need to decide on the perfect gift, but there's a twist! Hitesh loves arrays, while Anirudh is fascinated by Binary Search Trees (BSTs). After some discussion, they realized Akash enjoys a specific type of BST — one that's created from an array that is the **preorder traversal** of the tree.

In the end, the challenge became clear:  

> **Given an array representing the preorder traversal of a BST**, your task is to reconstruct the tree and verify if the BST is correctly constructed.  

Help Hitesh and Anirudh decide on the gift by constructing the correct BST from the given preorder traversal! 🎁

---

## 📝 Problem Statement  

You are given a function `constructBST`, which takes an array as its parameter. This array is the preorder traversal of a Binary Search Tree (BST). Your task is to reconstruct the binary search tree from this preorder traversal and return the root of the tree.

**BST Properties:**  
- The left subtree contains nodes with keys less than the node's key.  
- The right subtree contains nodes with keys greater than the node's key.  
- Both subtrees are also binary search trees, ensuring all nodes have distinct keys.

---

## 📥 Input Format  
- First line: Integer `n` — number of elements in the preorder array.  
- Second line: `n` integers representing the preorder traversal of the BST.

---

## 📤 Output Format  
- Output `"YES"` if the reconstructed BST is correct, and `"NO"` if it's incorrect.

---

## 🧪 Example  

### 🔹 Testcase  
```
Input:  
5  
8 5 1 7 10

Output:  
YES
```

**Explanation:**  
The given preorder traversal is `[8, 5, 1, 7, 10]`.  
The correct BST should be constructed as follows:
```
      8
     / \
    5   10
   / \
  1   7
```

---

## ⚙️ Constraints  
- `1 ≤ n ≤ 100`  
- `1 ≤ preorder[i] ≤ 10⁹`  
- All values in the preorder array are **unique**.

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

// Global index to keep track of current node in preorder array
int idx = 0;

// Function to build BST from preorder traversal
Node* buildBST(vector<int>& preorder, int minVal, int maxVal) {
    if (idx >= preorder.size()) return NULL;

    int val = preorder[idx];
    if (val < minVal || val > maxVal) return NULL;

    Node* root = new Node(val);
    idx++;
    
    root->left = buildBST(preorder, minVal, val - 1);
    root->right = buildBST(preorder, val + 1, maxVal);

    return root;
}

Node* constructBST(vector<int>& preorder) {
    idx = 0;
    return buildBST(preorder, INT_MIN, INT_MAX);
}

// Function to check if a BST is correctly constructed (in-order check)
pair<int,int> f(Node* root, bool &flag){
    if(!root) return {INT_MAX, INT_MIN};
    
    pair<int,int> lt = f(root->left,flag);
    pair<int,int> rt = f(root->right,flag);
    
    if(root->val <= lt.second || root->val >= rt.first){
        flag = false;
    }
    
    return {min({root->val, lt.first, rt.first}), max({root->val, lt.second, rt.second})};
}

bool isBST(Node* root){
    bool flag = true;
    f(root,flag);
    return flag;
}

// Function to get preorder traversal from the BST
void getPreorderTraversal(Node* root,vector<int>& arr){
    if(!root) return;
    arr.push_back(root->val);
    getPreorderTraversal(root->left,arr);
    getPreorderTraversal(root->right,arr);
}

// Function to check if the BST is correct
bool checkAnswer(Node* root,vector<int>& preorder){
    vector<int> arr;
    getPreorderTraversal(root,arr);
    return (arr == preorder) && isBST(root);
}

int main() {
    int n;
    cin >> n;
    
    vector<int> preorder(n);
    for(int &x : preorder) cin >> x;
    
    Node *root = constructBST(preorder);

    if(checkAnswer(root, preorder)) cout << "YES";
    else cout << "NO";
}
```

---

## 🏷️ Tags  
`🌳 Binary Search Tree` | `🔄 Preorder Traversal` | `🔄 BST Reconstruction` | `📚 Recursion`

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

🎉 **Help Anirudh and Hitesh win Akash's wedding gift challenge by constructing the correct BST!** 🎁