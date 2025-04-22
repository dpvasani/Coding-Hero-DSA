# 📌 DSA Sheet – 5 : ✅ The Curious Case of the Missing Numbers
## 🎯 Problem Level  
**Medium**

---

## 🧩 Background  

Hitesh, Anirudh, and Akash are preparing for a coding competition, and they stumble upon an interesting puzzle while building a Binary Search Tree (BST) from a set of unique numbers. Anirudh, the curious one, has inserted several numbers into the BST. Now, Hitesh challenges Akash with a question:

"Hey Akash! Between two given numbers L and R, can you find the K-th smallest number that's missing from the BST?"

Akash, being the problem-solver of the group, agrees — but with a condition: Hitesh must allow him to use his own logic.

The Challenge:
Anirudh has already created the BST using N unique integers.
Hitesh picks a range [L, R] and asks Akash to find the K-th smallest number that should have been in the range but isn't present in the BST. If there aren't K missing numbers in the range, Akash should return -1.

---

## 📝 Problem Statement  

You are given a Binary Search Tree (BST) constructed using N unique integers.  
Hitesh picks a range [L, R] and asks Akash to find the K-th smallest missing number in the given range, i.e., between L and R.

If there aren't enough missing numbers in the range, return -1.

Implement the function `solve(TreeNode* root, int L, int R, int K)` that returns the K-th smallest missing number.

---  

## 📥 Input Format  
- The first line contains an integer `N` — the number of nodes in the BST.
- The second line contains `N` integers representing the level-order traversal of the BST. Use `-1` to represent missing nodes.
- The third line contains three integers `L`, `R`, and `K`, representing the range [L, R] and the K-th smallest missing number.

---

## 📤 Output Format  
- Output the K-th smallest missing number in the range [L, R], or `-1` if there aren't enough missing numbers.

---

## 🧪 Example  

### 🔹 Testcase  
```
Input:  
7  
5 3 8 1 4 6 10  
3 10 3

Output:  
4
```

**Explanation:**  
- The BST formed is:
  ```
        5
       / \
      3   8
     / \  / \
    1  4 6  10
  ```

- In the range [3, 10], the numbers present are {3, 4, 5, 6, 8, 10}.  
- The numbers that should ideally be there are {3, 4, 5, 6, 7, 8, 9, 10}.  
- Missing numbers are {7, 9}.  
- The 3rd missing number is `4`.

---

## ⚙️ Constraints  
- `1 ≤ N ≤ 100`  
- `1 ≤ L, R ≤ 10^9`  
- `0 ≤ Node.val ≤ 10^9`  
- All node values are **unique**.

---

## 💻 C++ Solution  

```cpp
#include<bits/stdc++.h>
using namespace std;

struct TreeNode {
    int val;
    TreeNode *left;
    TreeNode *right;
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
};

// Inorder Traversal function to find numbers in the range [L, R]
void inorder(TreeNode* root, int L, int R, vector<int>& missing) {
    if (!root) return;
    
    inorder(root->left, L, R, missing);
    
    // Add numbers in the range [L, R] to the list
    if (root->val >= L && root->val <= R) {
        missing.push_back(root->val);
    }
    
    inorder(root->right, L, R, missing);
}

int solve(TreeNode* root, int L, int R, int K) {
    vector<int> present;
    inorder(root, L, R, present);  // Get numbers in the range [L, R]
    
    int prev = L - 1;  // Start from just before L
    int count = 0;
    
    // Find the missing numbers in the range
    for (int num : present) {
        while (prev + 1 < num) {
            prev++;
            count++;
            if (count == K) return prev;  // K-th missing number
        }
        prev = num;
    }
    
    // If there are missing numbers after the last present number
    while (prev + 1 <= R) {
        prev++;
        count++;
        if (count == K) return prev;
    }
    
    return -1;  // If not enough missing numbers
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
    int L, R, K;
    cin >> L >> R >> K;
    TreeNode* root = buildTree(input);
    cout << solve(root, L, R, K) << endl;
    return 0;
}
```

---

## 🏷️ Tags  
`🌳 Binary Tree` | `🔍 Inorder Traversal` | `📚 Missing Numbers` | `⏱️ Optimization` | `🧠 Logic-based Problem`

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

☕ Let’s solve the curious case of missing numbers! 😄