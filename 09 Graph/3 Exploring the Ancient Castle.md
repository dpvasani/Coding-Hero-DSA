# 📌 DSA Sheet – 3 : ✅ Exploring the Ancient Castle  
## 🎯 Problem Level  
**Medium**

---

## 🧩 Background  

Hitesh and Piyush are exploring an ancient castle that is rumored to contain several hidden rooms. The castle is represented as a grid, where each square is either part of the floor or a solid wall. Hitesh, with his knack for solving puzzles, and Piyush, an avid explorer, need your help to map out the rooms of the castle.

A room is defined as a contiguous area of floor squares connected horizontally or vertically.

---

## 📝 Problem Statement  

You are given a map of the castle, represented as a grid of size `n x m`. Each square is marked with either a `.` (floor) or `#` (wall). You need to determine the number of distinct rooms in the castle. A room is defined as a contiguous area of floor squares connected horizontally or vertically.

---

## 📥 Input Format  
- Two integers `n` and `m` (1 ≤ n, m ≤ 1000) — the dimensions of the grid.
- An `n x m` grid, where each cell is either `.` (floor) or `#` (wall).

---

## 📤 Output Format  
- Output a single integer representing the number of distinct rooms in the castle.

---

## 🧪 Example  

### 🔹 Testcase  
```
Input:  
5 8  
.#..#...  
..#..#..  
.#....#.  
.#..#...  
....#...  

Output:  
3
```

**Explanation:**  
The grid represents a map of the castle, and the function will count the number of distinct rooms formed by contiguous `.` (floor) squares.

---

## ⚙️ Constraints  
- 1 ≤ n, m ≤ 1000  
- Each square is either a `.` or a `#`.

---

## 💻 C++ Solution  

```cpp
#include <bits/stdc++.h>
using namespace std;

vector<vector<int>> visited;
int dir[4][2] = {{-1,0}, {1,0}, {0,-1}, {0,1}};

void dfs(int i, int j, int n, int m, vector<vector<char>>& grid) {
    visited[i][j] = 1;
    for(int d = 0; d < 4; d++) {
        int x = i + dir[d][0];
        int y = j + dir[d][1];
        if(x >= 0 && x < n && y >= 0 && y < m && !visited[x][y] && grid[x][y] == '.') {
            dfs(x, y, n, m, grid);
        }
    }
}

int countRooms(int n, int m, vector<vector<char>>& grid) {
    visited.assign(n, vector<int>(m, 0));
    int rooms = 0;
    
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < m; j++) {
            if(!visited[i][j] && grid[i][j] == '.') {
                rooms++;
                dfs(i, j, n, m, grid);
            }
        }
    }
    
    return rooms;
}

// Main function to execute the solution
int main() {
    int n, m;
    cin >> n >> m;
    
    vector<vector<char>> graph(n, vector<char>(m));
    for(int i = 0; i < n; i++) {
        string s;
        cin >> s;
        for(int j = 0; j < m; j++) {
            graph[i][j] = s[j];
        }
    }
    
    cout << countRooms(n, m, graph);
}
```

---

## 🏷️ Tags  
`🏰 Grid` | `🚶‍♂️ DFS` | `🏠 Room Counting` | `🧠 Recursion`

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

☕ Help Hitesh and Piyush explore the ancient castle and find all the rooms! 🏰