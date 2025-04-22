# 📌 DSA Sheet – 6 : ✅ The Silent Sum of Missing Numbers  
## 🎯 Problem Level  
**Medium**

---

## 🧩 Background  

Hitesh, Anirudh, and Akash are exploring the hidden sum of missing numbers in a Binary Search Tree (BST). Anirudh has constructed the BST using unique integers. Hitesh challenges Akash with a new puzzle:

"Hey Akash! Between two numbers L and R, can you find the sum of all numbers that should exist in this range but are missing from the BST?"

Akash, being the problem-solver, agrees but insists on using his optimized approach.

---

## 📝 Problem Statement  

You are given a Binary Search Tree (BST) constructed using N unique integers. Hitesh provides a range [L, R] and asks Akash to find the sum of all integers in the range [L, R] that are missing from the BST.

If no numbers are missing, return `0`.

Implement the function `solve(TreeNode* root, int L, int R)` that returns the sum of all missing numbers in the given range.

---

## 📥 Input Format  
- The first line contains an integer `N` — the number of nodes in the BST.
- The second line contains `N` integers representing the level-order traversal of the BST. Use `-1` to represent missing nodes.
- The third line contains two integers `L` and `R`, representing the range [L, R].

---

## 📤 Output Format  
- Output the sum of missing numbers in the range [L, R], or `0` if no numbers are missing.

---

## 🧪 Example  

### 🔹 Testcase  

**Input:**  
```
BST contains: {2, 5, 7, 10}
Range: [1, 10]
```

**Output:**  
```
31
```

**Explanation:**  
- The BST contains `{2, 5, 7, 10}`.
- The range [1, 10] has the numbers {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}.
- The missing numbers in the BST are {1, 3, 4, 6, 8, 9}.
- The sum of missing numbers is: 1 + 3 + 4 + 6 + 8 + 9 = 31.

---

## ⚙️ Constraints  
- `1 ≤ N ≤ 100`
- `1 ≤ L, R ≤ 10^9`
- `0 ≤ Node.val ≤ 10^9`
- All node values are **unique**.

---

## 💻 C++ Solution  

```cpp
#include <bits/stdc++.h>
using namespace std;

struct TreeNode {
    int val;
    TreeNode *left;
    TreeNode *right;
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
};

// Inorder traversal function to get all numbers in the BST
void inorder(TreeNode* root, vector<int>& sorted) {
    if (!root) return;
    inorder(root->left, sorted);
    sorted.push_back(root->val);
    inorder(root->right, sorted);
}

long long solve(TreeNode* root, int L, int R) {
    vector<int> sorted;
    inorder(root, sorted);
    
    // Start checking for missing numbers
    long long missingSum = 0;
    int prev = L - 1;  // Start from the number before L
    
    for (int i = 0; i < sorted.size(); ++i) {
        // Check if there are any missing numbers between prev and sorted[i]
        while (prev + 1 < sorted[i]) {
            prev++;
            if (prev >= L && prev <= R) {
                missingSum += prev;  // Add missing number to the sum
            }
        }
        // Update prev to the current sorted number
        prev = sorted[i];
    }
    
    // Check if there are any remaining missing numbers after the last element in sorted
    while (prev + 1 <= R) {
        prev++;
        missingSum += prev;
    }
    
    return missingSum;
}

TreeNode* buildTree(vector<int>& input) {
    if (input.empty() || input[0] == -1) return nullptr;
    TreeNode* root = new TreeNode(input[0]);
    queue<TreeNode*> q;
    q.push(root);
    int i = 1;
    while (!q.empty() && i < input.size()) {
        TreeNode* curr = q.front();
        q.pop();
        // Left child
        if (i < input.size() && input[i] != -1) {
            curr->left = new TreeNode(input[i]);
            q.push(curr->left);
        }
        i++;
        // Right child
        if (i < input.size() && input[i] != -1) {
            curr->right = new TreeNode(input[i]);
            q.push(curr->right);
        }
        i++;
    }
    return root;
}

int main() {
    int N;
    cin >> N;
    vector<int> input(N);
    for (int& x : input) cin >> x;
    int L, R;
    cin >> L >> R;
    TreeNode* root = buildTree(input);
    cout << solve(root, L, R);
    return 0;
}
```

---

## 🏷️ Tags  
`🌳 Binary Search Tree` | `🔢 Missing Numbers` | `📚 Inorder Traversal` | `🔍 Optimization`

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

☕ Let’s solve the silent sum of missing numbers! 😄

--- 
