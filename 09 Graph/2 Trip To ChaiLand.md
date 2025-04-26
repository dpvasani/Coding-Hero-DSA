# 📌 **Coding Hero Sheet – 2** : ✅ **Trip To ChaiLand**  
## 🎯 **Problem Level**  
**Medium**

---

## 🧩 **Background**  

Shreya came across a tricky implementation challenge. She discovered a secret map of **ChaiLand**, where every city and road had a name. She wants to start in a particular city **S** and travel to the **holy-capital-city T**, by using the minimum number of roads.  
ChaiLand was planned algorithmically such that there is at most **1 shortest path** between city S and city T. It has **N cities** in total, with **M uni-directional roads**.

Your task is to help Shreya find the shortest path in terms of roads (if possible) and print the roads she will take. If no such path exists, print **"Impossible"**.

---

## 📝 **Problem Statement**  

Given a map of cities and roads in ChaiLand, your task is to:
- Find the shortest path from the source city **S** to the destination city **T**, in terms of roads.
- If the journey is not possible, print **"Impossible"**.

### Constraints:
- **1 ≤ N ≤ 1000** (number of cities)
- **1 ≤ M ≤ 10^6** (number of roads)
- Each road has a name of length ≤ 10.
- The cities and roads are represented as strings.

### Example:

#### Input 1:
```
5 6
xor-city list-city kunal-road
matrix-city xor-city agni-path
list-city matrix-city pallav-maarg
matrix-city graph-city manvendra-road
xor-city graph-city
```

#### Output 1:
```
3
kunal-road
pallav-maarg
manvendra-road
```

#### Input 2:
```
7
A B C D a b c
5
B
C
D
a
b
c
```

#### Output 2:
```
Impossible
```

---

## ⚙️ **C++ Solution**  

```cpp
#include <bits/stdc++.h>
using namespace std;

void solve(int N, int M, vector<vector<string>>& roadRelation, string& src, string& tar) {
    // Create an adjacency list to represent the graph
    unordered_map<string, vector<pair<string, string>>> adj;  // city -> (neighbor, road_name)
    
    // Populate the adjacency list
    for (int i = 0; i < M; i++) {
        string from = roadRelation[i][0];
        string to = roadRelation[i][1];
        string road = roadRelation[i][2];
        adj[from].push_back({to, road});
    }
    
    // BFS to find the shortest path from src to tar
    queue<string> q;
    unordered_map<string, string> parent;  // to store the parent of each city
    unordered_map<string, bool> visited;  // to check if a city is visited
    unordered_map<string, string> roadTaken;  // to track the road taken to each city
    
    q.push(src);
    visited[src] = true;
    parent[src] = "";
    
    bool found = false;
    
    while (!q.empty()) {
        string city = q.front();
        q.pop();
        
        if (city == tar) {
            found = true;
            break;
        }
        
        for (auto& neighbor : adj[city]) {
            string nextCity = neighbor.first;
            string roadName = neighbor.second;
            
            if (!visited[nextCity]) {
                visited[nextCity] = true;
                parent[nextCity] = city;
                roadTaken[nextCity] = roadName;
                q.push(nextCity);
            }
        }
    }
    
    // If there's no path from src to tar, print "Impossible"
    if (!found) {
        cout << "Impossible" << endl;
        return;
    }
    
    // Reconstruct the path
    vector<string> path;
    string current = tar;
    
    while (current != src) {
        string road = roadTaken[current];
        path.push_back(road);
        current = parent[current];
    }
    
    reverse(path.begin(), path.end());
    
    // Output the result
    cout << path.size() << endl;
    for (const string& road : path) {
        cout << road << endl;
    }
}

// Don't Change Any code Outside the Solve Function

int main() {
    int N, M;
    cin >> N >> M;
    
    vector<vector<string>> grid(M);
    
    for (int i = 0; i < M; i++) {
        string from, to, road;
        cin >> from >> to >> road;
        grid[i].push_back(from);
        grid[i].push_back(to);
        grid[i].push_back(road);
    }

    string src, dest;
    cin >> src >> dest;
    
    solve(N, M, grid, src, dest);

    return 0;
}
```

---

## 🧪 **Explanation of Solution**  

1. **Graph Representation:**  
   - We represent the cities and roads using an **adjacency list** where each city points to its neighbors, and each edge (road) has a name.

2. **Breadth-First Search (BFS):**  
   - We use BFS to find the shortest path from the source city **S** to the destination city **T**. BFS is ideal for finding the shortest path in an unweighted graph (since we just care about the number of roads).

3. **Tracking the Path:**  
   - We maintain a `parent` map to keep track of the previous city for each city, allowing us to reconstruct the path once we reach the destination.
   - We also maintain a `roadTaken` map to store the names of the roads leading to each city.

4. **Reconstructing the Path:**  
   - If we find a path, we backtrack from **T** to **S** using the `parent` map, collecting the roads in reverse order. After that, we reverse the collected roads to get the correct order.

5. **Edge Case – No Path:**  
   - If no path exists from **S** to **T**, we print **"Impossible"**.

---

## 🏷️ **Tags**  
`🌐 Graph` | `🛣️ Shortest Path` | `🗺️ BFS` | `🚧 Road Path` | `🔍 Search Algorithm`

---

## 👨‍💻 **Author**  

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

☕ **Enjoy coding! Keep solving problems like a coding hero!** 😄