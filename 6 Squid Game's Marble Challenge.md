# 🧩 DSA Sheet – Problem 6: Squid Game's Marble Challenge

## 🎯 Problem Level  
**Medium**

---

## 📚 Problem Background  

In the **Squid Game's infamous Marble Challenge**, players bet marbles on a mysterious board of **pits**, each holding a number of marbles.

A player can collect marbles only from a **contiguous range** of pits in one move. With limited time and **multiple queries**, you must quickly determine the **sum of marbles** from pit `l` to pit `r`.

You’ve been recruited by the **Front Man** to calculate these totals efficiently before the clock runs out.

---

## 📝 Problem Statement  

Given:
- An array of integers where each element represents the number of marbles in a pit.
- A set of queries where each query asks for the **sum of marbles between two pit indices** (inclusive).  

Your task is to process all queries **efficiently** and output the result for each.

---

## 📥 Input Format  

- The first line contains two integers:  
  - `n`: the number of pits  
  - `q`: the number of queries  

- The second line contains `n` space-separated integers, each representing the number of marbles in a pit.  

- The next `q` lines each contain two integers `l` and `r` (1-based indexing), denoting the **inclusive** range for the query.

---

## 📤 Output Format  

- For each query, print a single integer:  
  the total number of marbles in the range `[l, r]`.

---

## 🧪 Example  

### 🔹 Input  
```
5 3  
1 2 3 4 5  
1 3  
2 5  
1 5  
```

### 🔹 Output  
```
6  
14  
15  
```

### 🧠 Explanation  
- Query 1: 1 + 2 + 3 = 6  
- Query 2: 2 + 3 + 4 + 5 = 14  
- Query 3: 1 + 2 + 3 + 4 + 5 = 15  

---

## ⚙️ Constraints  

- `1 ≤ n, q ≤ 10^5`  
- `1 ≤ marbles[i] ≤ 10^3`  
- Use **prefix sum** for O(1) query time.

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <vector>

using namespace std;

vector<int> processQueries(int n, const vector<int>& marbles, const vector<pair<int, int>>& queries) {
    vector<int> prefixSum(n + 1, 0);

    // Compute prefix sum
    for (int i = 1; i <= n; i++) {
        prefixSum[i] = prefixSum[i - 1] + marbles[i - 1];
    }

    // Answer queries in O(1)
    vector<int> results;
    for (const auto& query : queries) {
        int l = query.first, r = query.second;
        results.push_back(prefixSum[r] - prefixSum[l - 1]);
    }

    return results;
}

int main() {
    int n, q;
    cin >> n >> q;

    vector<int> marbles(n);
    for (int i = 0; i < n; i++) {
        cin >> marbles[i];
    }

    vector<pair<int, int>> queries(q);
    for (int i = 0; i < q; i++) {
        int l, r;
        cin >> l >> r;
        queries[i] = {l, r};
    }

    vector<int> results = processQueries(n, marbles, queries);
    for (int res : results) {
        cout << res << endl;
    }

    return 0;
}
```

---

## 🏷️ Tags  
`🎯 Prefix Sum` | `💡 Range Query` | `📈 Cumulative Sum` | `⚡ Optimization`

---

## 👨‍💻 Author  

### 🚀 **Darshan Vasani**  
💡 **Full-Stack Developer | Software Engineer | Mentor**   

### 🌐 Connect with Me  
- **Website:** [dpvasani56.vercel.app](https://dpvasani56.vercel.app)  
- **GitHub:** [@dpvasani](https://github.com/dpvasani)  
- **LinkedIn:** [@dpvasani56](https://www.linkedin.com/in/dpvasani56/)  
- **Topmate:** [topmate.io/dpvasani56](https://topmate.io/dpvasani56)  
- **Linktree:** [linktr.ee/dpvasani56](https://linktr.ee/dpvasani56)  
- **Twitter/X:** [@vasanidarshan56](https://x.com/vasanidarshan56)  
- **Credly:** [@dpvasani57](https://www.credly.com/users/dpvasani57/)

---
