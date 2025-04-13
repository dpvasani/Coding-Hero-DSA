
# 🧩 DSA Sheet – Problem 3: K Closest Points to Origin

## 🎯 Problem Level  
**Medium**

---

## 📚 Problem Background  

You're developing a **mapping application** that needs to find the nearest **points of interest** to a user's current location. This feature is foundational for apps like **Google Maps**, **Zomato**, or **Uber**, where finding nearby results quickly is key to performance.

To implement this, you are tasked with building a function that identifies the **k closest points to the origin (0, 0)** using the **Euclidean distance** formula.

---

## 📝 Problem Statement  

Given:
- An array `points` where each point is represented as a pair of integers `[x, y]`.
- An integer `k`.

Your task is to return the `k` closest points to the origin `(0, 0)` based on Euclidean distance.

**Distance formula**:  
For a point `(x, y)`, the distance from the origin is calculated as:  
`sqrt(x² + y²)`  
*(Note: To compare distances, using the squared distance is sufficient and avoids unnecessary square root calculations.)*

Return the answer in **any order**.

---

## 📥 Input Format  

- `points`: A 2D vector of integers, where each subarray contains two integers `[x, y]`.
- `k`: An integer representing the number of closest points to return.

---

## 📤 Output Format  

- A 2D vector of the `k` closest points to the origin.

---

## 🧪 Example  

### 🔹 Example 1  

**Input**  
```
points = [[1, 3], [-2, 2]], k = 1
```

**Output**  
```
[[-2, 2]]
```

**Explanation**  
- Distance of (1,3) = √10 ≈ 3.16  
- Distance of (-2,2) = √8 ≈ 2.83  
→ Since √8 < √10, the closest point is `[-2, 2]`.

---

## ⚙️ Constraints  

- `1 ≤ points.length ≤ 10^4`  
- `-10^4 ≤ points[i][0], points[i][1] ≤ 10^4`  
- `1 ≤ k ≤ points.length`

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <vector>
#include <queue>
#include <cmath>
#include <string>
#include <sstream>
using namespace std;

// Function to calculate squared Euclidean distance
double squaredDistance(const vector<int>& point) {
    return point[0] * point[0] + point[1] * point[1];
}

vector<vector<int>> kClosest(vector<vector<int>>& points, int k) {
    // Max-heap to store k closest points by distance
    priority_queue<pair<double, vector<int>>> maxHeap;

    for (const auto& point : points) {
        double dist = squaredDistance(point);

        if (maxHeap.size() < k) {
            maxHeap.push({dist, point});
        } else if (dist < maxHeap.top().first) {
            maxHeap.pop();
            maxHeap.push({dist, point});
        }
    }

    vector<vector<int>> result;
    while (!maxHeap.empty()) {
        result.push_back(maxHeap.top().second);
        maxHeap.pop();
    }

    return result;
}

int main() {
    string input;
    getline(cin, input);

    try {
        size_t pipePos = input.find('|');
        if (pipePos == string::npos) {
            cout << "Invalid input";
            return 0;
        }

        string pointsStr = input.substr(0, pipePos);
        string kStr = input.substr(pipePos + 1);
        int k = stoi(kStr);

        vector<vector<int>> points;
        size_t start = pointsStr.find('[');
        size_t end = pointsStr.find_last_of(']');

        if (start != string::npos && end != string::npos) {
            string content = pointsStr.substr(start + 1, end - start - 1);
            size_t pos = 0;

            while ((pos = content.find('[', pos)) != string::npos) {
                size_t endPos = content.find(']', pos);
                if (endPos != string::npos) {
                    string pointStr = content.substr(pos + 1, endPos - pos - 1);
                    vector<int> point;
                    stringstream ss(pointStr);
                    string value;
                    while (getline(ss, value, ',')) {
                        point.push_back(stoi(value));
                    }
                    if (point.size() == 2) {
                        points.push_back(point);
                    }
                    pos = endPos + 1;
                } else {
                    break;
                }
            }
        }

        vector<vector<int>> result = kClosest(points, k);

        cout << "[";
        for (size_t i = 0; i < result.size(); i++) {
            cout << "[" << result[i][0] << "," << result[i][1] << "]";
            if (i < result.size() - 1) {
                cout << ",";
            }
        }
        cout << "]";
    } catch (const exception&) {
        cout << "Invalid input";
    }

    return 0;
}
```

---

## 🏷️ Tags  
`📍 Geometry` | `📊 Priority Queue` | `⚙️ Heap` | `📦 Sorting` | `📌 2D Arrays`

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

🚀 **Follow me for more cool DSA problems & solutions!** 🌟  

---  
