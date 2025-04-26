
# 📌 DSA Sheet – 4: 🛠️ Break Walls I

## 🎯 Problem Level  
**Medium**

---

## 🧩 Background  

In the heart of a bustling city, **Hitesh**, an innovative urban planner 🏙️, faces a unique challenge.  
The city is represented as a **grid**, where his **office** (`'O'`) and **home** (`'H'`) are located at different spots.  

The city is jam-packed with **walls (`'#'`)** and **free spaces (`'.'`)**. Hitesh must design the **most efficient route** from his office to his home. 🏢🏠  
However, the challenge is that **walls block the way** — and **he can break them if necessary**.  
**Breaking a wall costs 1**, and **free spaces cost 0** to move through.

Can you help Hitesh find the **minimum number of walls** he must break to go home? 🚶‍♂️🛠️

---

## 📝 Problem Statement  

You are given:
- A grid of size `n x m`.
- Each cell can be:
  - `'O'` → Office (start point)
  - `'H'` → Home (destination)
  - `'.'` → Free space
  - `'#'` → Wall

Find the **minimum number of walls** that need to be broken to create a path from the office to the home.

You can move **up**, **down**, **left**, and **right** — but **not diagonally**.

---

## 📥 Input Format  
- First line: Two integers `n` and `m` — dimensions of the grid.
- Next `n` lines: Each line contains a string of length `m` describing the grid.

---

## 📤 Output Format  
- Output a single integer — the **minimum number of walls** that must be broken.

---

## 🧪 Example  

### 🔹 Testcase  
```
Input:
5 5
O.#..
..#.#
##..#
#..#H
#....

Output:
1
```

**Explanation:**  
- The best path requires **breaking only 1 wall**.
- Hitesh carefully navigates through the free spaces and **breaks minimum walls**! 🧱✨

---

## ⚙️ Constraints  
- `1 ≤ n, m ≤ 1000`
- There is **exactly one office** and **exactly one home** in the grid.

---

## 💻 C++ Solution  

```cpp
#include <bits/stdc++.h>
using namespace std;

int minWallsToBreak(int n, int m, vector<vector<char>>& grid) {
    // Directions: up, down, left, right
    int dir[4][2] = {{-1,0},{1,0},{0,-1},{0,1}};
    
    // Find Office and Home locations
    int sx = -1, sy = -1, ex = -1, ey = -1;
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < m; j++) {
            if(grid[i][j] == 'O') {
                sx = i, sy = j;
            } else if(grid[i][j] == 'H') {
                ex = i, ey = j;
            }
        }
    }
    
    // 0-1 BFS (walls cost 1 to break, free space cost 0)
    deque<pair<int, pair<int, int>>> dq; // {walls_broken, {x, y}}
    vector<vector<int>> dist(n, vector<int>(m, INT_MAX));
    
    dq.push_front({0, {sx, sy}});
    dist[sx][sy] = 0;
    
    while(!dq.empty()) {
        auto [walls, pos] = dq.front();
        dq.pop_front();
        int x = pos.first;
        int y = pos.second;
        
        for(int d = 0; d < 4; d++) {
            int nx = x + dir[d][0];
            int ny = y + dir[d][1];
            
            if(nx >= 0 && ny >= 0 && nx < n && ny < m) {
                int cost = (grid[nx][ny] == '#') ? 1 : 0;
                if(dist[nx][ny] > walls + cost) {
                    dist[nx][ny] = walls + cost;
                    if(cost == 0) {
                        dq.push_front({dist[nx][ny], {nx, ny}});
                    } else {
                        dq.push_back({dist[nx][ny], {nx, ny}});
                    }
                }
            }
        }
    }
    
    return dist[ex][ey];
}

int main() {
    int n, m;
    cin >> n >> m;
    
    vector<vector<char>> grid(n, vector<char>(m));
    
    for(int i = 0; i < n; i++) {
        string s;
        cin >> s;
        for(int j = 0; j < m; j++) {
            grid[i][j] = s[j];
        }
    }
    
    cout << minWallsToBreak(n, m, grid);
    
    return 0;
}
```

---

## 🏷️ Tags  
`🏙️ Grid Traversal` | `🔍 0-1 BFS` | `🛠️ Walls Breaking` | `🛣️ Shortest Path`

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

🌟 Help Hitesh demolish the least number of walls and reach home faster! 🌟

---
