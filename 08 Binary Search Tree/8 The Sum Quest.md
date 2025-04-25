# 📌 DSA Sheet – 8 : ✅ The Sum Quest  
## 🎯 Problem Level  
**Hard**

---

## 🧩 Background  

Akash and Anirudh are at "The Code Nook" café, working on a coding challenge. Akash presents a problem that involves finding the maximum sum of keys in any Binary Search Tree (BST) within a given binary tree. The BST must have all its left nodes' keys less than the root and all right nodes' keys greater. Your task is to help them solve the problem and handle special cases like negative values or single-node trees.

---

## 📝 Problem Statement  

You are given a binary tree. Your task is to find the **maximum sum of keys** in any valid **Binary Search Tree (BST)** that exists within the given binary tree. A subtree is considered a BST if:
- All left nodes' keys are smaller than the root node.
- All right nodes' keys are greater than the root node.

Implement the function:  
`long long getMaxSumBST(Node* root)`  
Where `Node` is the node structure of the binary tree.

### 🔍 Example:  

**Input:**  
```
Binary Tree: {10, 5, 15, 3, 7, -1, 18}
```

**Output:**  
```
35
```

**Explanation:**  
The maximum sum of a BST is the subtree `{5, 3, 7}`, whose sum is `5 + 3 + 7 = 35`.  
Other subtrees like `{10, 5, 15}` are not valid BSTs.

---

## ⚙️ Constraints  
- The number of nodes in the tree is in the range [1, 1000].  
- Node values range from `-10^9` to `10^9`.  
- All node values in the BST are unique.

---

## 💻 C++ Solution  

```cpp
#include <bits/stdc++.h>
using namespace std;

struct Node {
    long long val;
    Node *left, *right;
    Node(long long x) : val(x), left(NULL), right(NULL) {}
    Node() : val(0LL), left(NULL), right(NULL) {}
    Node(int x,Node* left,Node* right) : val(x), left(left), right(right) {}
};

struct SubtreeInfo {
    bool isBST;
    long long sum;
    long long minVal;
    long long maxVal;
};

// Helper function that returns whether the subtree is a BST, its sum, and its min/max values
SubtreeInfo getBSTInfo(Node* root) {
    if (!root) {
        // A null tree is a valid BST, with a sum of 0 and no min/max values
        return {true, 0, LLONG_MAX, LLONG_MIN};
    }

    // Recursively get info for the left and right subtrees
    SubtreeInfo leftInfo = getBSTInfo(root->left);
    SubtreeInfo rightInfo = getBSTInfo(root->right);

    // A subtree is a BST if:
    // - Left subtree is a BST
    // - Right subtree is a BST
    // - The root's value is greater than the maximum value of the left subtree
    // - The root's value is less than the minimum value of the right subtree
    bool isBST = leftInfo.isBST && rightInfo.isBST && root->val > leftInfo.maxVal && root->val < rightInfo.minVal;

    // If it is a BST, calculate the sum and update the min/max values
    if (isBST) {
        return {true, root->val + leftInfo.sum + rightInfo.sum,
                min(root->val, leftInfo.minVal), max(root->val, rightInfo.maxVal)};
    } else {
        // If not a BST, return an invalid BST with 0 sum and extreme min/max
        return {false, 0, 0, 0};
    }
}

long long getMaxSumBST(Node* root) {
    long long maxSum = 0;

    // Helper function to perform the post-order traversal and track the maximum sum of valid BSTs
    function<void(Node*)> dfs = [&](Node* node) {
        if (!node) return;

        // Get the BST info for the current subtree
        SubtreeInfo info = getBSTInfo(node);

        // If the subtree is a valid BST, update the maxSum
        if (info.isBST) {
            maxSum = max(maxSum, info.sum);
        }

        // Traverse the left and right subtrees
        dfs(node->left);
        dfs(node->right);
    };

    // Start the DFS from the root
    dfs(root);
    return maxSum;
}

// Helper function to build the binary tree from an input array
Node* getBinaryTree(vector<int>& arr) {
    if (arr.size() == 0) return NULL;

    queue<Node*> qu;
    Node* root = new Node(arr[0]);
    qu.push(root);
    int idx = 1;

    while (idx < arr.size()) {
        auto curr = qu.front();
        qu.pop();

        if (arr[idx] == -1) {
            curr->left = NULL;
        } else {
            curr->left = new Node(arr[idx]);
            qu.push(curr->left);
        }
        idx++;

        if (arr[idx] == -1) {
            curr->right = NULL;
        } else {
            curr->right = new Node(arr[idx]);
            qu.push(curr->right);
        }
        idx++;
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

    Node* root = getBinaryTree(nodeValues);

    cout << getMaxSumBST(root);

    return 0;
}
```

---

## 🏷️ Tags  
`🌳 Binary Search Tree` | `💡 Dynamic Programming` | `🧠 Subtree Calculations` | `🔍 Maximum Sum` | `🚀 Tree Traversals`

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

☕ Ready to tackle the next coding challenge? 😄

---