# 📌 DSA Sheet – Problem 2: ❓ Minimum Time To Complete Tasks  
## 🎯 Problem Level  
**Medium**

---

## 🧩 Background  

The problem involves a task scheduler that processes multiple tasks. Each task has a certain processing time, and the scheduler can run multiple instances of the same task simultaneously. The goal is to minimize the time required to complete all tasks by optimally allocating available instances.

The concept uses the **Ceil Division** to figure out how much time it takes to complete each task based on the number of instances allocated, ensuring that the total number of instances used does not exceed the maximum available.

---

## 📝 Problem Statement  

You are given `n` tasks, each with a processing time. You also have a total of `maxInstances` available instances. Your goal is to find the minimum time required to complete all tasks by optimally allocating the instances.

For each task with processing time `t`, if `k` instances are assigned, the task will complete in `ceil(t / k)` time.

Write a function to determine the **minimum time** to complete all tasks.

---

## 📥 Input Format  
- Two integers `n` and `maxInstances` — the number of tasks and the maximum available instances.
- The second line contains `n` integers representing the processing time of each task.

```
Input:  
n maxInstances  
task_1 task_2 ... task_n
```

---

## 📤 Output Format  
- A single integer representing the minimum time to complete all tasks.

---

## 🧪 Example  

### 🔹 Example 1  
```
Input:  
3 5  
2 4 8  

Output:  
4
```

**Explanation:**  
We are given 3 tasks with processing times [2, 4, 8] and a total of 5 instances.  
For `t = 4`, the allocation of instances is:  
- Task 1 (2): `ceil(2 / 4) = 1` instance  
- Task 2 (4): `ceil(4 / 4) = 1` instance  
- Task 3 (8): `ceil(8 / 4) = 2` instances  

Total instances needed = 1 + 1 + 2 = 4 ≤ 5  
Thus, the tasks can be completed in **4 time units**.

---

## ⚙️ Constraints  
- `1 ≤ n ≤ 10^5`  
- `1 ≤ maxInstances ≤ 10^9`  
- `1 ≤ task_i ≤ 10^9`  

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <vector>
#include <cmath>
#include <algorithm>

using namespace std;

bool isPossible(int time, const vector<int>& tasks, int maxInstances) {
    long long totalInstances = 0;
    for (int t : tasks) {
        totalInstances += (t + time - 1) / time; // Equivalent to ceil(t / time)
        if (totalInstances > maxInstances) return false;
    }
    return true;
}

int minTimeToComplete(vector<int>& tasks, int maxInstances) {
    int left = 1, right = *max_element(tasks.begin(), tasks.end());
    int answer = right;

    while (left <= right) {
        int mid = left + (right - left) / 2;

        if (isPossible(mid, tasks, maxInstances)) {
            answer = mid;         // Try for better (lower) time
            right = mid - 1;
        } else {
            left = mid + 1;       // Need more time
        }
    }

    return answer;
}

int main() {
    int n, maxInstances;
    cin >> n >> maxInstances;
    
    vector<int> tasks(n);
    for (int i = 0; i < n; i++) {
        cin >> tasks[i];
    }
    
    cout << minTimeToComplete(tasks, maxInstances);
    return 0;
}
```

---

## 🏷️ Tags  
`📚 Binary Search` | `📈 Arrays` | `⏳ Time Optimization` | `🚀 Instance Allocation`

---

## 👨‍💻 Author  

### 🚀 **Darshan Vasani**  
💡 **Full-Stack Developer | Software Engineer | Mentor**    

### 🔗 Connect with me! 🌍  
🌐 **Portfolio:** [dpvasani56.vercel.app](https://dpvasani56.vercel.app/)  
🐙 **GitHub:** [github.com/dpvasani](https://github.com/dpvasani)  
💼 **LinkedIn:** [linkedin.com/in/dpvasani56](https://www.linkedin.com/in/dpvasani56/)  
🌳 **Linktree:** [linktr.ee/dpvasani56](https://linktr.ee/dpvasani56)  
🎓 **Credly:** [credly.com/users/dpvasani57](https://www.credly.com/users/dpvasani57/)  
🐦 **Twitter:** [x.com/vasanidarshan56](https://x.com/vasanidarshan56)  
📢 **Topmate:** [topmate.io/dpvasani56](https://topmate.io/dpvasani56)  

---

🔥 **Stay tuned for more clean and optimized DSA patterns!** 💡

---