# 📌 DSA Sheet – 5: 🛤️  Travelling Couples

## 🎯 Problem Level  
**Hard**

---

## 🧩 Background  

In the magical land of **Chailand**, **Akash** and his wife **Meera** are stranded in two separate cities. Their goal is to get home, but there are multiple cities connected by enchanted bidirectional train routes. These routes allow them to travel using three types of magical tickets:

- **Ticket Type I (C1):** Costs `C1` coins, but can only be used by males like Akash.
- **Ticket Type II (C2):** Costs `C2` coins, but can only be used by females like Meera.
- **Ticket Type III (C3):** Costs `C3` coins, and can only be used by couples traveling together from the same city.

Akash starts in **city 1**, and Meera starts in **city 2**. They both need to reach **city N**. The challenge is to minimize the total cost of tickets, whether they travel separately or together.

---

## 📝 Problem Statement  

You are given:
- Three integers `C1`, `C2`, `C3` — the costs of the three ticket types.
- Two integers `N` (number of cities) and `M` (number of train routes).
- A list of `M` bidirectional train routes between cities, where each route connects two cities.

The goal is to find the **minimum total cost** Akash and Meera need to spend to both reach **city N**.

You can:
- Akash can travel using **Ticket Type I** or **Ticket Type III**.
- Meera can travel using **Ticket Type II** or **Ticket Type III**.
- Both can travel separately or together but both must reach city N.

---

## 📥 Input Format  
- First line: Five space-separated integers `C1`, `C2`, `C3`, `N`, `M` — the costs of the ticket types, number of cities, and number of train routes.
- Next `M` lines: Each line contains two space-separated integers `u` and `v` representing a bidirectional train route between city `u` and city `v`.

---

## 📤 Output Format  
- Output a single integer — the **minimum total cost** Akash and Meera must spend to both reach city N.

---

## 🧪 Example  

### 🔹 Testcase  
```
Input:
4 5 8 8 6
1 2
2 3
3 4
4 5
5 6
6 7
7 8
Output:
22
```

**Explanation:**  
The optimal strategy involves:
- Akash travels from city 1 to city 4 with a male-only ticket (cost 4).
- Meera travels from city 2 to city 3, then city 3 to city 4 using female-only tickets (cost 4 + 4).
- Akash and Meera meet in city 4 and use couple tickets to travel together to city 7 and 8 (cost 5 + 5).

The total cost is: `4 + (4 + 4) + (5 + 5) = 22`.

---

## ⚙️ Constraints  
- `1 ≤ C1, C2, C3 ≤ 10^6`
- `3 ≤ N ≤ 10^5`
- The map is fully connected — every city can be reached from any other city through some series of train rides.

---

## 💻 C++ Solution  

```cpp
#include <bits/stdc++.h>
using namespace std;

void BFS(vector<int>& distance, int src, vector<vector<int>>& adj) {
    distance[src] = 0;
    queue<int> q;
    q.push(src);
    while (!q.empty()) {
        int node = q.front();
        q.pop();
        for (auto neighbor : adj[node]) {
            if (distance[neighbor] == INT_MAX) {
                distance[neighbor] = distance[node] + 1;
                q.push(neighbor);
            }
        }
    }
}

int solve(int C1, int C2, int C3, int N, int M, vector<pair<int, int>>& Edges) {
    vector<vector<int>> adj(N); // 0-based indexing

    for (auto& edge : Edges) {
        int u = edge.first - 1; // 0-based index
        int v = edge.second - 1;
        adj[u].push_back(v);
        adj[v].push_back(u);
    }

    vector<int> distFrom1(N, INT_MAX); // distance from node 1 (0-based)
    vector<int> distFrom2(N, INT_MAX); // distance from node 2 (0-based)
    vector<int> distFromN(N, INT_MAX); // distance from node N (0-based)

    BFS(distFrom1, 0, adj);     // starting from node 1 (index 0)
    BFS(distFrom2, 1, adj);     // starting from node 2 (index 1)
    BFS(distFromN, N - 1, adj); // starting from node N (index N-1)

    long long minCost = LLONG_MAX;

    for (int i = 0; i < N; ++i) {
        if (distFrom1[i] != INT_MAX && distFrom2[i] != INT_MAX && distFromN[i] != INT_MAX) {
            long long cost = 1LL * distFrom1[i] * C1 + 1LL * distFrom2[i] * C2 + 1LL * distFromN[i] * C3;
            minCost = min(minCost, cost);
        }
    }

    return (minCost == LLONG_MAX ? -1 : static_cast<int>(minCost));
}

int main() {
    int C1, C2, C3, N, M;
    cin >> C1 >> C2 >> C3 >> N >> M;

    vector<pair<int, int>> Edges(M);
    for (int i = 0; i < M; i++) {
        int u, v;
        cin >> u >> v;
        Edges[i] = {u, v};
    }

    cout << solve(C1, C2, C3, N, M, Edges);
    return 0;
}
```

---

## 🏷️ Tags  
`🌍 Graph Traversal` | `🔍 BFS` | `💸 Cost Optimization` | `🚂 Train Routing` | `🛤️ Pathfinding`  

---

## 👨‍💻 Author  

### 🚀 **Darshan Vasani**  
💡 **Full-Stack Developer | Software Engineer | Mentor**  

### 🔗 Connect with me! 🌍  
🌐 **Portfolio:** [dpvasani56.vercel.app](https://dpvasani56.vercel.app)  
🐙 **GitHub:** [github.com/dpvasani](https://github.com/dpvasani)  
💼 **LinkedIn:** [linkedin.com/in/dpvasani56](https://linkedin.com/in/dpvasani56)  
🌳 **Linktree:** [linktr.ee/dpvasani56](https://linktr.ee/dpvasani56)  
🎓 **Credly:** [credly.com/users/dpvasani57](https://credly.com/users/dpvasani57)  
🐦 **Twitter:** [x.com/vasanidarshan56](https://x.com/vasanidarshan56)  
📢 **Topmate:** [topmate.io/dpvasani56](https://topmate.io/dpvasani56)

---  

🌟 Help Akash and Meera travel with minimal costs and reunite at their cozy home! 🌟