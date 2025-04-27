# 📌 DSA Sheet – 7 :🚧 Metropolis Bridge Restoration

## 🎯 Problem Level  
**Hard**

---

## 🧩 Background  

In the grand city of **Metropolis**, there are **n districts** connected by **m bridges**. Due to years of neglect, all the bridges are in such disrepair that they cannot be used. The city council has tasked you with restoring some of the bridges so that there is a path (possibly through other districts) between every pair of districts. Each bridge has a specific restoration cost.

Your goal is to select a set of bridges to repair such that every district can be reached from every other district (directly or indirectly), and the total repair cost is minimized. If it is impossible to connect all the districts, return **-1**.

---

## 📝 Problem Statement  

You are given:
- `n` districts numbered from `1` to `n`.
- `m` bridges, where each `bridges[i] = [a, b, c]` denotes a two-way bridge between districts `a` and `b` with a restoration cost of `c`.

Your task is to return the **minimum total restoration cost** required to connect all districts, or **-1** if it cannot be done.

---

## 📥 Input Format  
- The first line contains two integers `n` and `m` — number of districts and number of bridges.  
- The next `m` lines contain three integers `a`, `b`, `c` — representing a two-way bridge between districts `a` and `b` with a restoration cost of `c`.

---

## 📤 Output Format  
- Output the **minimum total restoration cost** required to connect all districts.  
- If it is impossible to connect all districts, return `-1`.

---

## 🧪 Example  

### 🔹 Testcase 1  
```
Input:
4 5
1 2 3
2 3 1
3 4 2
4 1 4
1 3 5

Output:
6
```

**Explanation**  
The optimal set of bridges to repair connects all districts with a total cost of 6, which includes bridges:  
- `1 <-> 2` (cost 3)  
- `2 <-> 3` (cost 1)  
- `3 <-> 4` (cost 2)  

---

## ⚙️ Constraints  
- `1 ≤ n ≤ 10^5`
- `1 ≤ m ≤ 2×10^5`
- `1 ≤ c ≤ 10^9`
- No two bridges connect the same pair of districts.
- Each bridge goes between two different districts.

---

## 💻 C++ Solution  

```cpp
#include <bits/stdc++.h>
using namespace std;

vector<vector<int>> Edges; 
vector<int> parent, rankk;

// Find parent of a node with path compression
int find_parent(int x) {
    if (x == parent[x]) return x;
    return parent[x] = find_parent(parent[x]);
}

// Union by rank for merging sets
void addEdge(int u, int v) {
    u = find_parent(u);
    v = find_parent(v);
    if (u != v) {
        if (rankk[u] >= rankk[v]) {
            parent[v] = u;
            rankk[u] += rankk[v];
        } else {
            parent[u] = v;
            rankk[v] += rankk[u];
        }
    }
}

// Function to find the minimum restoration cost to connect all districts
int minRestorationCost(int n, vector<vector<int>>& bridges) {
    int m = bridges.size();
    
    // Initialize parent and rank for Union-Find
    Edges.clear();
    parent.resize(n + 1);
    rankk.resize(n + 1, 1);
    for (int i = 1; i <= n; i++) {
        parent[i] = i;
    }

    // Create the edges with cost and district numbers
    for (int i = 0; i < m; i++) {
        int a = bridges[i][0], b = bridges[i][1], c = bridges[i][2];
        Edges.push_back({c, a, b});  // {cost, district1, district2}
    }

    // Sort the edges based on the cost
    sort(Edges.begin(), Edges.end());

    int ans = 0;

    // Apply Kruskal's algorithm to find MST
    for (auto& x : Edges) {
        int c = x[0], a = x[1], b = x[2];
        
        // If they belong to the same set, skip
        if (find_parent(a) != find_parent(b)) {
            addEdge(a, b);  // Merge the sets
            ans += c;  // Add the cost of this bridge to the result
        }
    }

    // Check if all districts are connected
    int cc = 0;
    for (int i = 1; i <= n; i++) {
        if (find_parent(i) == 1) cc++;
    }

    // If not all districts are connected, return -1
    return (cc > 1 ? -1 : ans);
}

int main() {
    int n, m;
    cin >> n >> m;
    
    vector<vector<int>> bridges(m, vector<int>(3));
    for (int i = 0; i < m; i++) {
        cin >> bridges[i][0] >> bridges[i][1] >> bridges[i][2];
    }

    cout << minRestorationCost(n, bridges);

    return 0;
}
```

---

## 🏷️ Tags  
`🌍 Graph` | `💸 Minimum Spanning Tree` | `🔗 Kruskal's Algorithm` | `💡 Union-Find` | `🚧 Optimization`

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

🌟 Help restore the bridges and connect the districts of Metropolis! 🌟

---