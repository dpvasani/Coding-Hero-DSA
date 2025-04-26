# 📌 DSA Sheet – 6 : 🚧 Avoiding Cursed Cities

## 🎯 Problem Level  
**Medium**

---

## 🧩 Background  

In the mystical land of **ChaiLand**, our heroes **Naman** and **Akash** are planning an epic road trip. 🚗✨  
However, danger lurks: some cities are **cursed**, and stepping into them would trap our heroes in an **eternal chai break**! ☕❌  

Given the map of ChaiLand with cities and two-way roads, help Naman and Akash find the **shortest safe path** from their starting city to their destination, **without** visiting any cursed cities.  
- Source and destination cities are **always safe**.
- Cursed cities **cannot be visited**.

Can you save their journey?

---

## 📝 Problem Statement  

You are given:
- `N` cities numbered `0` to `N-1`.
- `M` two-way roads connecting these cities.
- A list marking each city as **safe (0)** or **cursed (1)**.

Find the **minimum number of roads** Naman and Akash must travel to reach from `src` to `dest` **without visiting any cursed cities**.

If it is **impossible** to reach the destination safely, output `-1`.

---

## 📥 Input Format  
- First line: Two integers `N` and `M` — number of cities and number of roads.  
- Second line: Two integers `src` and `dest` — starting and ending city.  
- Third line: `N` integers — curse status of each city (`0` = safe, `1` = cursed).  
- Next `M` lines: Each line has two integers `u` and `v`, indicating a **two-way road** between city `u` and city `v`.

---

## 📤 Output Format  
- Output the **minimum number of roads** needed to reach from `src` to `dest` safely.
- If not possible, output `-1`.

---

## 🧪 Example  

### 🔹 Testcase  
```
Input:
5 5
0 2
0 1 0 0 0
0 1
1 2
0 3
3 4
4 2

Output:
3
```

**Explanation:**  
The road journey will be:  
`0 ➔ 3 ➔ 4 ➔ 2`  
- It takes **3 roads**.
- No cursed cities are entered. ✅

---

## ⚙️ Constraints  
- `1 ≤ N ≤ 10^5`
- `0 ≤ M ≤ 2×10^5`
- `0 ≤ src, dest < N`
- `curse[i]` is `0` or `1`
- `src` and `dest` will **never** be cursed.

---

## 💻 C++ Solution  

```cpp
#include <bits/stdc++.h>
using namespace std;

int Solve(int N, int M, int Src, int Dest, vector<int>& cursed, vector<pair<int, int>>& Edges) {
    // Create adjacency list
    vector<vector<int>> adj(N);
    for(auto &edge : Edges) {
        int u = edge.first;
        int v = edge.second;
        adj[u].push_back(v);
        adj[v].push_back(u);
    }
    
    // BFS Initialization
    vector<int> visited(N, 0);
    queue<pair<int, int>> q; // {current city, distance from src}

    q.push({Src, 0});
    visited[Src] = 1;

    while(!q.empty()) {
        auto [city, dist] = q.front();
        q.pop();

        if(city == Dest) return dist; // Found destination

        for(auto neighbor : adj[city]) {
            if(!visited[neighbor] && cursed[neighbor] == 0) {
                visited[neighbor] = 1;
                q.push({neighbor, dist + 1});
            }
        }
    }

    // Destination not reachable
    return -1;
}

int main() {
    int N, M, Src, Dest;
    cin >> N >> M >> Src >> Dest;
    vector<int> cursed(N);
    for (auto &it : cursed) cin >> it;

    vector<pair<int, int>> Edges;
    for (int i = 0; i < M; i++) {
        int u, v;
        cin >> u >> v;
        Edges.push_back({u, v});
    }

    cout << Solve(N, M, Src, Dest, cursed, Edges);

    return 0;
}
```

---

## 🏷️ Tags  
`🌍 Graph` | `🏃‍♂️ Shortest Path` | `🔍 BFS Traversal` | `🚫 Constraints Handling`

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

🌟 Save Naman and Akash from a never-ending chai break! Help them reach safely! 🌟

---

