# 📌 **Coding Hero Sheet – 1** : ✅ **The Graph Mission**  
## 🎯 **Problem Level**  
**Easy**

---

## 🧩 **Background**  

One bright morning, Hitesh, the ever-curious coder, stumbled upon a peculiar problem while exploring an old dusty book titled **"Adventures in Graphland"**.  

The book described a mysterious land where cities were connected in a strange way — not with roads, but with **numbers in a square grid**!

Hitesh rushed to his friends **Piyush** and **Prateek** and exclaimed:  
**"Guys! This grid is actually a Graph, represented as an Adjacency Matrix! We need to convert it into an Adjacency List to decode the connections between cities."**

Piyush, with a sparkle in his eye, replied:  
**"So basically, if there's a 1 at position (i, j) in the matrix, that means city i is connected to city j, right?"**

Prateek grinned, pulling out his laptop.  
**"Let's do it. For each city, let's list all other cities it connects to!"**

Your task is to help **Hitesh, Piyush**, and **Prateek** in transforming the matrix representation into a list format that clearly shows which cities are connected.

---

## 📝 **Problem Statement**  

Given an **Adjacency Matrix** representing a graph, your task is to convert it into an **Adjacency List** format.

### Constraints:
- The number of cities (N) is at most 1000.
- Each matrix element is either `0` (no connection) or `1` (connection exists).

### Example:

#### Input:
```
4
0111
1001
1001
1110
```

#### Output:
```
1: 2 3 4
2: 1 4
3: 1 4
4: 1 2 3
```

---

## ⚙️ **C++ Solution**  

```cpp
#include <bits/stdc++.h>
using namespace std;

void solve(int N, vector<vector<int>> grid) {
    // Write Your Code Here
    for (int i = 0; i < N; i++) {  // Loop through each node (city)
        cout << i + 1 << ":";  // Output node numbering starting from 1
        for (int j = 0; j < N; j++) {  // Loop through each possible connection
            if (grid[i][j]) {  // If there's a connection (1)
                cout << " " << j + 1;  // Output the connected city (1-based indexing)
            }
        }
        cout << '\n';  // Newline after printing the connections of each city
    }
}

// Don't Change Any code Outside the Solve Function

int main() {
    int N;
    cin >> N;  // Input the number of cities (nodes)
    vector<vector<int>> grid(N, vector<int>(N));  // Initialize the adjacency matrix

    // Read the adjacency matrix
    for (auto &it : grid) {
        for (auto &k : it) {
            cin >> k;
        }
    }

    solve(N, grid);  // Call the function to convert the matrix to the adjacency list

    return 0;
}
```

---

## 🧪 **Explanation of Solution**  

1. **Input Parsing:**  
   - We first input the number of cities `N` and then the adjacency matrix `grid` where each element represents a connection (1 means there's a connection, 0 means no connection).

2. **Iterate Over Cities:**  
   - We loop over each city (node), and for each city, we check which other cities it is connected to by inspecting the matrix for non-zero entries.

3. **Output the Adjacency List:**  
   - For each city `i`, if it is connected to city `j` (i.e., `grid[i][j] == 1`), we add `j + 1` (1-based indexing) to the adjacency list for city `i`.

4. **Printing the Results:**  
   - We print the adjacency list for each city in the required format.

---

## 🏷️ **Tags**  
`🌐 Graph` | `📊 Adjacency Matrix` | `🔄 Adjacency List` | `🧑‍💻 Coding Challenge` | `💻 Matrix Conversion`

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