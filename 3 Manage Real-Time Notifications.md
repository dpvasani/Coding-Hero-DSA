

# 📣 DSA Sheet – Problem 5: Manage Real-Time Notifications

## 🎯 Problem Level  
**Medium**  

---

## 📚 Problem Background  

You're working on a **SpringFest App** that sends out **notifications** to users about **events**, **offers**, and **updates**.  

Each notification belongs to a **category**, such as:  
- `"Event"`  
- `"Offer"`  
- `"Update"`  

Your job is to build a system that counts how many notifications are received **for each category**, and then displays the **counts sorted alphabetically** by category name.

---

## 📝 Problem Statement  

Given a list of notifications (strings) where each notification belongs to a category, write a program to:  
✅ Count the frequency of each category.  
✅ Return the result sorted **alphabetically by category name**.

---

## 📥 Input Format  

- `notifications`: A list of strings  
- `1 <= number of notifications <= 10^5`  
- Each string contains only **uppercase or lowercase letters**  
- `1 <= length of category name <= 50`

---

## 📤 Output Format  

An array of **objects**, where each object has:  
- `"category"`: the name of the category  
- `"count"`: the number of times it appeared  

🔡 The array must be **sorted alphabetically** by category name.

---

## 🧪 Example  

### 🔹 Input  
```
7  
Event  
Offer  
Event  
Update  
Offer  
Offer  
Event  
```

### 🔹 Output  
```json
[
  {"category": "Event", "count": 3}, 
  {"category": "Offer", "count": 3}, 
  {"category": "Update", "count": 1}
]
```

### 🧠 Explanation  
- "Event" → 3 times  
- "Offer" → 3 times  
- "Update" → 1 time  
- Alphabetical sort: **Event**, **Offer**, **Update**

---

## ⚙️ Constraints  

- `1 <= number of notifications <= 10^5`  
- `1 <= length of a category <= 50`  
- Categories contain only **English letters**

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <vector>
#include <string>
#include <map>
#include <algorithm>

using namespace std;

vector<pair<string, int>> countNotifications(const vector<string>& notifications) {
    map<string, int> categoryCount;

    // Count each category
    for (const string& category : notifications) {
        categoryCount[category]++;
    }

    // Convert map to a vector of pairs
    vector<pair<string, int>> result;
    for (const auto& entry : categoryCount) {
        result.push_back({entry.first, entry.second});
    }

    return result;
}

// Please don't touch the code below
int main() {
    int n;
    cin >> n;
    cin.ignore();  // Ignore newline character

    vector<string> notifications(n);
    for (int i = 0; i < n; i++) {
        getline(cin, notifications[i]);
    }

    vector<pair<string, int>> result = countNotifications(notifications);

    // Output in expected format
    cout << "[";
    for (size_t i = 0; i < result.size(); i++) {
        cout << "{\"category\": \"" << result[i].first << "\", \"count\": " << result[i].second << "}";
        if (i < result.size() - 1) cout << ", ";
    }
    cout << "]";

    return 0;
}
```

---

## 🏷️ Tags  
`📊 Map` | `🔁 Frequency Count` | `🔡 Sorting` | `📦 JSON Output Simulation`  

---

## 👨‍💻 Author  

### 🚀 **Darshan Vasani**  
💡 Full-Stack Developer | DSA Educator | Mentor  

### 🌐 Let's Connect  
- **Portfolio:** [dpvasani56.vercel.app](https://dpvasani56.vercel.app)  
- **GitHub:** [@dpvasani](https://github.com/dpvasani)  
- **LinkedIn:** [@dpvasani56](https://www.linkedin.com/in/dpvasani56/)  
- **Topmate:** [topmate.io/dpvasani56](https://topmate.io/dpvasani56)  
- **Linktree:** [linktr.ee/dpvasani56](https://linktr.ee/dpvasani56)  
- **Twitter/X:** [@vasanidarshan56](https://x.com/vasanidarshan56)  
- **Credly:** [@dpvasani55](https://www.credly.com/users/dpvasani55/)

---