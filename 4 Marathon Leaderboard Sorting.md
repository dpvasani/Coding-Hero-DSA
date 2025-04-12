# 📣 DSA Sheet – Problem 4: Marathon Leaderboard Sorting

## 🎯 Problem Level  
**Medium**

---

## 📚 Problem Background  

You're managing the **leaderboard** for a **Spring Marathon**. Runners are ranked based on their **completion time** in ascending order.  

If two runners complete the marathon in the **same time**, they are sorted **alphabetically** by their name.  

Your task is to implement a sorting function that displays the leaderboard correctly based on these criteria.

---

## 📝 Problem Statement  

Write a program to sort a list of marathon runners. Each runner is represented by:  
- `name`: A string representing the runner's name.  
- `time`: An integer representing the runner's completion time (in minutes).  

Sort the runners based on:  
✅ Completion time (ascending)  
✅ Name (alphabetically) if two runners have the same time  

---

## 📥 Input Format  

- An integer `n` denoting the number of runners  
- Followed by `n` lines where each line contains:  
  - `name` (string, 1 ≤ length ≤ 100)  
  - `time` (integer, 0 ≤ time ≤ 1000)

---

## 📤 Output Format  

- A sorted list of runners.  
- Each line contains the runner's `name` and `time` separated by a space.  
- The list should be sorted based on the given criteria.

---

## 🧪 Example  

### 🔹 Input  
```
3  
Alice 120  
Bob 115  
Charlie 120  
```

### 🔹 Output  
```
Bob 115  
Alice 120  
Charlie 120  
```

### 🧠 Explanation  
- Bob has the least time, so comes first.  
- Alice and Charlie have the same time, so they are sorted alphabetically.

---

## ⚙️ Constraints  

- `1 ≤ number of runners ≤ 100`  
- `0 ≤ time ≤ 1000`  
- `1 ≤ name length ≤ 100`  
- Names contain only English letters.

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

struct Runner {
    string name;
    int time;
};

// Comparison function defined outside the struct
bool compareRunners(const Runner& a, const Runner& b) {
    if (a.time == b.time) return a.name < b.name; // Sort alphabetically by name
    return a.time < b.time; // Otherwise, sort by time
}

vector<Runner> sortMarathonResults(vector<Runner> runners) {
    sort(runners.begin(), runners.end(), compareRunners);
    return runners;
}

// please don't touch the code below
int main() {
    int n;
    cin >> n;
    vector<Runner> runners(n);

    for (int i = 0; i < n; i++) {
        cin >> runners[i].name >> runners[i].time;
    }

    vector<Runner> sortedRunners = sortMarathonResults(runners);

    for (const auto& runner : sortedRunners) {
        cout << runner.name << " " << runner.time << endl;
    }

    return 0;
}
```

---

## 🏷️ Tags  
`🏃 Sorting` | `🧮 Comparator` | `📋 Structs` | `📈 Leaderboard Logic`

---

## 👨‍💻 Author  

### 🚀 **Darshan Vasani**  
💡 **Full-Stack Developer | Software Engineer | Mentor**   

### 🌐 Let's Connect  
- **Portfolio:** [dpvasani56.vercel.app](https://dpvasani56.vercel.app)  
- **GitHub:** [@dpvasani](https://github.com/dpvasani)  
- **LinkedIn:** [@dpvasani56](https://www.linkedin.com/in/dpvasani56/)  
- **Topmate:** [topmate.io/dpvasani56](https://topmate.io/dpvasani56)  
- **Linktree:** [linktr.ee/dpvasani56](https://linktr.ee/dpvasani56)  
- **Twitter/X:** [@vasanidarshan56](https://x.com/vasanidarshan56)  
- **Credly:** [@dpvasani57](https://www.credly.com/users/dpvasani57/)

---
