# 📌 DSA Sheet – 7 : ✅ Missing Median  
## 🎯 Problem Level  
**Hard**

---

## 🧩 Background  

Hitesh, Piyush, and Anirudh are back with another BST brain-teaser!  
Anirudh builds a Binary Search Tree (BST) using unique integers. But of course, Piyush has a trick up his sleeve.

"Hey Hitesh! Between two numbers L and R, what's the **median** of all the **missing numbers** from your BST?"  
If there are two medians, choose the **smaller** one!

Hitesh is fired up and ready to outsmart Piyush. Can you help Hitesh find that elusive **missing median**?

---

## 📝 Problem Statement  

Given a Binary Search Tree (BST) created from a level-order array (with `-1` representing `null`), and a range `[L, R]`, find the **median** of all numbers in `[L, R]` that are **not present** in the BST.

Return:
- The **median of missing numbers**.
- If no numbers are missing, return `-1`.

### 🔍 Median Rule:
- If the count of missing numbers is **odd**, return the **middle** element.
- If the count is **even**, return the **smaller of the two middle elements**.

Implement the function:  
`int solve(TreeNode* root, int L, int R)`

---

## 📥 Input Format  
- The first line contains an integer `M` — the number of nodes in the level-order representation (including `-1` for nulls).
- The second line contains `M` space-separated integers — level-order traversal of the BST.
- The third line contains two integers `L` and `R`.

---

## 📤 Output Format  
- Output the median of the missing numbers in the range `[L, R]`.
- If there are no missing numbers, print `-1`.

---

## 🧪 Example  

### 🔹 Testcase  

**Input:**  
```
BST: {5, 2, 7, -1, -1, -1, 10}
Range: [1, 10]
```

**Output:**  
```
4
```

**Explanation:**  
- BST contains: `{2, 5, 7, 10}`  
- Range [1, 10] contains: `{1, 2, 3, 4, 5, 6, 7, 8, 9, 10}`  
- Missing numbers: `{1, 3, 4, 6, 8, 9}`  
- Sorted missing numbers → 6 values → Median (even count) = smaller of middle two → **4**

---

## ⚙️ Constraints  
- `1 ≤ M ≤ 100`  
- `1 ≤ L, R ≤ 10^9`  
- All values in the BST are **unique**  
- Use `-1` to represent null children in level-order

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

void collectValues(TreeNode* root, unordered_set<int>& present) {
    if (!root) return;
    present.insert(root->val);
    collectValues(root->left, present);
    collectValues(root->right, present);
}

int solve(TreeNode* root, int L, int R) {
    unordered_set<int> present;
    collectValues(root, present);

    vector<int> missing;
    for (int i = L; i <= R; ++i) {
        if (present.find(i) == present.end()) {
            missing.push_back(i);
        }
    }

    if (missing.empty()) return -1;

    int n = missing.size();
    return missing[n / 2 - (n % 2 == 0 ? 1 : 0)]; // smaller median if even
}

TreeNode* buildTree(vector<int>& input) {
    if (input.empty() || input[0] == -1) return nullptr;
    TreeNode* root = new TreeNode(input[0]);
    queue<TreeNode*> q;
    q.push(root);
    int i = 1;
    while (!q.empty() && i < input.size()) {
        TreeNode* curr = q.front(); q.pop();
        if (i < input.size() && input[i] != -1) {
            curr->left = new TreeNode(input[i]);
            q.push(curr->left);
        }
        i++;
        if (i < input.size() && input[i] != -1) {
            curr->right = new TreeNode(input[i]);
            q.push(curr->right);
        }
        i++;
    }
    return root;
}

int main() {
    int M;
    cin >> M;
    vector<int> input(M);
    for (int i = 0; i < M; ++i) cin >> input[i];
    int L, R;
    cin >> L >> R;
    TreeNode* root = buildTree(input);
    cout << solve(root, L, R);
    return 0;
}
```

---

## 🏷️ Tags  
`🌳 Binary Search Tree` | `🧠 Median` | `🔢 Missing Numbers` | `📊 Sorted Arrays` | `🧠 Logic`

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

☕ Ready to find the next median mystery? 😄

--- 
