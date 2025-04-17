# 📌 DSA Sheet – Problem 5: ❓ Minimum Speed to Arrive on Time  
## 🎯 Problem Level  
**Medium**

---

## 🧩 Background  

You are planning a **train journey** that consists of `n` segments. For every segment except the last, the train must **arrive at an integer time**, meaning if the time is fractional, it is **rounded up**. The last segment can be fractional.

To complete the journey within a given **maximum time (`hours`)**, you need to determine the **minimum integer speed `v`** such that the train reaches the destination on or before time.

This is a classic **binary search on answer** problem — we use binary search to find the minimum speed that satisfies the time constraint by checking if a candidate speed is sufficient.

---

## 📝 Problem Statement  

You are given an integer `n`, a double `hours`, and an array `distances[]` of length `n`, where `distances[i]` represents the distance of the `i-th` segment of a train journey.

- The travel time for a segment is `distances[i] / v`, where `v` is the train speed.
- For all segments except the last one, round up travel time to the nearest **integer**.
- For the last segment, use **actual decimal** time.
- Return the **minimum integer speed `v`** such that the total time is ≤ `hours`.  
If it is **impossible**, return `-1`.

---

## 📥 Input Format  
- Two values: `n` (number of segments), and `hours` (maximum journey time)  
- Followed by `n` space-separated integers representing `distances`

```
Input:  
n hours  
distances[0] distances[1] ... distances[n-1]
```

---

## 📤 Output Format  
- A single integer: the **minimum speed** needed to finish the journey within time, or `-1` if not possible.

---

## 🧪 Example  

### 🔹 Example 1  
```
Input:  
3 6.0  
1 3 2

Output:  
1
```

**Explanation:**  
For speed = 1 km/h:  
- Segment 1: ceil(1/1) = 1  
- Segment 2: ceil(3/1) = 3  
- Segment 3: 2/1 = 2  

Total time = 1 + 3 + 2 = **6.0**, which is allowed.

---

## ⚙️ Constraints  
- `1 ≤ n ≤ 10⁵`  
- `1 ≤ distances[i] ≤ 10⁵`  
- `1 ≤ hours ≤ 10⁹`  
- `hours` has at most **two decimal places**

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <vector>
#include <cmath>
using namespace std;

bool canReachOnTime(const vector<int>& distances, double hours, int speed) {
    double totalTime = 0.0;
    int n = distances.size();

    for (int i = 0; i < n - 1; ++i) {
        totalTime += ceil((double)distances[i] / speed);
    }
    totalTime += (double)distances[n - 1] / speed;

    return totalTime <= hours;
}

int minSpeedToArrive(vector<int>& distances, double hours) {
    int left = 1, right = 1e7;
    int answer = -1;

    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (canReachOnTime(distances, hours, mid)) {
            answer = mid;
            right = mid - 1;
        } else {
            left = mid + 1;
        }
    }

    return answer;
}

int main() {
    int n;
    double hours;
    cin >> n >> hours;

    vector<int> distances(n);
    for (int i = 0; i < n; ++i) {
        cin >> distances[i];
    }

    cout << minSpeedToArrive(distances, hours);
    return 0;
}
```

---

## 🏷️ Tags  
`🚄 Binary Search on Answer` | `📈 Arrays` | `⏱️ Time Calculation` | `🔁 Rounding Logic`  

---

## 👨‍💻 Author  

### 🚀 **Darshan Vasani**  
💡 **Full-Stack Developer | Software Engineer | Mentor**  

### 🔗 Connect with me! 🌍  
🌐 **Portfolio:** [dpvasani56.vercel.app](https://dpvasani56.vercel.app)  
🐙 **GitHub:** [github.com/dpvasani](https://github.com/dpvasani)  
💼 **LinkedIn:** [linkedin.com/in/dpvasani56](https://www.linkedin.com/in/dpvasani56/)  
🌳 **Linktree:** [linktr.ee/dpvasani56](https://linktr.ee/dpvasani56)  
🎓 **Credly:** [credly.com/users/dpvasani55](https://www.credly.com/users/dpvasani55/)  
🐦 **Twitter:** [x.com/vasanidarshan56](https://x.com/vasanidarshan56)  
📢 **Topmate:** [topmate.io/dpvasani56](https://topmate.io/dpvasani56)

---

🔥 **Stay tuned for more clean and optimized DSA patterns!** 💡

---