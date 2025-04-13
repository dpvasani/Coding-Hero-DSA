
# 🧩 DSA Sheet – Problem 13: 🛒 Order Management System for Electronics Returns — C++ Challenge

## 🧠 Problem Level  
**Medium**

---

## 🧩 Background  

As an **SDE at Meta**, you've been tasked with identifying **influential users** in a **directed graph** representation of a social network.  
Each **user** is a node, and each **"follows" relationship** is a directed edge from one user to another.

Your goal is to compute the **most influential user** — the one with the **maximum number of followers**.

This user will be the **top target for marketing**, so accuracy and efficiency are both critical.

If there's a tie in influence scores, the **user with the smallest ID** should be selected.

---

## 📝 Problem Statement  

You are given:
- `n` users labeled from `0` to `n-1`
- `m` directed edges, where an edge `u → v` means user `u` follows user `v`

You need to:
- Compute the **influence score** for each user (number of followers)
- Return the **user ID** with the **highest influence score**
- If multiple users have the same score, return the **smallest user ID**

---

## 📥 Input Format  

- First line: Two integers `n` (number of users) and `m` (number of connections)  
- Next `m` lines: Two integers `u` and `v` — a directed edge from `u` to `v`

---

## 📤 Output Format  
- A single integer: the ID of the **most influential user**

---

## 🧪 Example  

### 🔹 Example Input  
```
5 6  
0 2  
1 2  
2 2  
3 2  
4 2  
4 3
```

### 🔹 Example Output  
```
2
```

### 🧠 Explanation  
- User 2 has 4 followers (from 0, 1, 3, 4)  
- Self-loop `2→2` is ignored  
- No one else has more than 1 follower  
✅ So, output is **2**

---

## ⚙️ Constraints  

- `1 ≤ n ≤ 10^5`  
- `0 ≤ m ≤ 10^6`  
- `0 ≤ u, v < n`  
- Self-loops and duplicate edges **may exist**, but **only count unique followers**

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <vector>
using namespace std;

// Function to return user with highest influence
int mostInfluentialUser(vector<int> influenceScore) {
    int maxInfluence = -1;
    int userId = -1;

    for (int i = 0; i < influenceScore.size(); i++) {
        if (influenceScore[i] > maxInfluence) {
            maxInfluence = influenceScore[i];
            userId = i;
        } else if (influenceScore[i] == maxInfluence && i < userId) {
            userId = i;
        }
    }

    return userId;
}

int main() {
    int n, m;
    cin >> n >> m;

    vector<int> influenceScore(n, 0);

    for (int i = 0; i < m; i++) {
        int u, v;
        cin >> u >> v;
        if (u != v) {
            influenceScore[v]++;
        }
    }

    cout << mostInfluentialUser(influenceScore);
    return 0;
}
```

---

## 🏷️ Tags  
`📊 Graphs` | `📈 Influence Analysis` | `➡️ Directed Edges` | `👥 Social Network`

---

## 👨‍💻 Author  

### 🚀 **Darshan Vasani**  
🎯 Full-Stack Developer | C++ + DSA Enthusiast | Mentor & Open Source Contributor  

### 🔗 Stay Connected  
- 🌐 [dpvasani56.vercel.app](https://dpvasani56.vercel.app)  
- 🧑‍💻 [GitHub](https://github.com/dpvasani)  
- 💼 [LinkedIn](https://linkedin.com/in/dpvasani56)  
- 📞 [Topmate](https://topmate.io/dpvasani56)  
- 🧵 [Twitter](https://x.com/vasanidarshan56)

---