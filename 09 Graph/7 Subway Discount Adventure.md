# 📌 DSA Sheet – 7 : 🚇 Subway Discount Adventure

## 🎯 Problem Level  
**Hard**

---

## 🧩 Background  

In the bustling city of **Metrotown**, **Akash** is determined to visit his best friend **Hitesh** at the far edge of the city. 🚆 But, there’s a twist! Akash has a **discount token** that can halve the fare of any subway ride during his journey. However, the catch is that he can only use it **once**. Your task is to help Akash travel from **Station 1** to **Station n** in the **cheapest possible way**, taking full advantage of the discount.

---

## 📝 Problem Statement  

You are given:
- `n` stations numbered from `1` to `n`.
- A list `rides` where each entry `[a, b, c]` represents a **directed subway ride** from **station a** to **station b** with a fare of **c**.

Your task is to compute the **minimum total fare** required for Akash to travel from **station 1** to **station n**, considering he can use the discount on **any one ride** (rounding down if the fare is odd).

---

## 📥 Input Format  
- The first line contains two integers, `n` (number of stations) and `m` (number of subway rides).
- The next `m` lines contain three integers `a`, `b`, and `c` representing a subway ride from station `a` to station `b` with a fare `c`.

---

## 📤 Output Format  
- Output the **minimum total fare** needed for Akash to travel from **station 1** to **station n**.
- If it is impossible, output `-1`.

---

## 🧪 Example  

### 🔹 Testcase  
```
Input:
3 3
1 2 31
2 3 11
1 3 71

Output:
2
```

**Explanation:**  
Akash can take:
- **Station 1 ➔ Station 2** (Fare 31, with discount: pay 15)
- **Station 2 ➔ Station 3** (Fare 11, pay full)

Total cost: **15 + 1 = 2** (the cheapest route).

---

## ⚙️ Constraints  
- `1 ≤ n ≤ 10^5`
- `1 ≤ m ≤ 2×10^5`
- `1 ≤ c ≤ 10^9`

---

## 💻 C++ Solution  

```cpp
#include <bits/stdc++.h>
using namespace std;

// Function to perform Dijkstra's algorithm
vector<int> dijkstra(int n, int src, bool flag, vector<vector<pair<int, int>>>& graph, vector<vector<pair<int, int>>>& rgraph) {
    vector<int> dist(n + 1, 1e9);  // distance to each node, initialized to INF
    dist[src] = 0;
    vector<int> visited(n + 1, 0);
    priority_queue<pair<int, int>> pq;
    pq.push({-dist[src], src});
    
    while (!pq.empty()) {
        auto curr = pq.top();
        pq.pop();
        if (visited[curr.second] == 1) continue;
        visited[curr.second] = 1;
        
        if (flag) {
            // Traverse the original graph
            for (auto &neigh : graph[curr.second]) {
                int edgeWeight = neigh.second;
                if (dist[neigh.first] > dist[curr.second] + edgeWeight) {
                    dist[neigh.first] = dist[curr.second] + edgeWeight;
                    pq.push({-dist[neigh.first], neigh.first});
                }
            }
        } else {
            // Traverse the reverse graph
            for (auto &neigh : rgraph[curr.second]) {
                int edgeWeight = neigh.second;
                if (dist[neigh.first] > dist[curr.second] + edgeWeight) {
                    dist[neigh.first] = dist[curr.second] + edgeWeight;
                    pq.push({-dist[neigh.first], neigh.first});
                }
            }
        }
    }
    
    return dist;
}

int minSubwayFare(int n, vector<vector<int>>& rides) {
    int m = rides.size();
    vector<vector<pair<int, int>>> graph(n + 1);  // Original graph
    vector<vector<pair<int, int>>> rgraph(n + 1);  // Reverse graph
    
    // Build the graph and reverse graph
    for (int i = 0; i < m; i++) {
        int a = rides[i][0], b = rides[i][1], c = rides[i][2];
        graph[a].push_back({b, c});
        rgraph[b].push_back({a, c});
    }

    // Step 1: Dijkstra from station 1 (forward direction)
    vector<int> dist1 = dijkstra(n, 1, true, graph, rgraph);

    // Step 2: Dijkstra from station n (reverse direction)
    vector<int> dist2 = dijkstra(n, n, false, graph, rgraph);

    int ans = INT_MAX;
    // Step 3: Try applying the discount to each ride and calculate the cost
    for (int i = 0; i < m; i++) {
        int a = rides[i][0], b = rides[i][1], c = rides[i][2];
        int discountedFare = c / 2;  // Halve the fare for the discount
        
        // The total cost if we use the discount on this ride
        ans = min(ans, dist1[a] + discountedFare + dist2[b]);
    }

    return ans;
}

int main() {
    int n, m;
    cin >> n >> m;
    vector<vector<int>> rides(m, vector<int>(3));
    
    // Reading the rides input
    for (int i = 0; i < m; i++) {
        cin >> rides[i][0] >> rides[i][1] >> rides[i][2];
    }
    
    // Output the result of the minimum subway fare
    cout << minSubwayFare(n, rides) << endl;
    return 0;
}
```

---

## 🏷️ Tags  
`🌍 Graph` | `🏃‍♂️ Shortest Path` | `💸 Discount` | `🔍 Dijkstra` | `🔄 Reverse Graph`

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

🌟 Help Akash reach Hitesh with the cheapest fare! 🌟

---