

# 🧩 DSA Sheet – Problem 11: 📺 Smart Stream Quality Selector

## 🎯 Problem Level  
**Medium**

---

## 📚 Problem Background  

You’re working at **Dreamflix**, a next-gen streaming service. A key feature of the platform is its **adaptive streaming engine**, which adjusts video quality based on available bandwidth.

Your job is to implement the logic that:
1. Automatically selects the **highest quality video** that **does not exceed** the current bandwidth.
2. Returns **"No Quality Available"** if all options require more bandwidth.

This ensures **optimal viewing experience**—no buffering, and no unnecessarily low-quality streams.

---

## 📝 Problem Statement  

Given:
- A user's current bandwidth (`b`) in kbps.
- A list of video qualities, each with:
  - `quality` → name of the quality (e.g., "720p", "1080p", "4K")
  - `required` → minimum bandwidth needed for that quality

Return the **best (highest) quality** that fits within the available bandwidth.

---

## 📥 Input Format  

- An integer `b` representing the user's current bandwidth in kbps.  
- An integer `n`, the number of video qualities available.  
- Followed by `n` lines, each containing:  
  - a `string` (quality name)  
  - an `integer` (required bandwidth)

---

## 📤 Output Format  

- A single string:  
  - Highest video quality stream that can be played smoothly  
  - Or `"No Quality Available"` if nothing fits

---

## 🧪 Example  

### 🔹 Example 1  

**Input**  
```
5000  
4  
4K 15000  
1080p 5000  
720p 3000  
480p 1000  
```

**Output**  
```
1080p
```

**Explanation**  
The bandwidth is 5000 kbps.  
Available options under 5000 are: `480p`, `720p`, `1080p`  
→ `1080p` is the highest valid choice.

---

## ⚙️ Constraints  

- `1 ≤ n ≤ 10^3`  
- `0 ≤ required ≤ 10^5`  
- `0 ≤ b ≤ 10^5`  
- Qualities may not be sorted in input.

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <vector>
#include <string>
#include <algorithm>

using namespace std;

struct Quality {
    string quality;
    int required;
};

// Function to select the highest stream quality within the bandwidth
string selectStreamQuality(int bandwidth, vector<Quality>& qualities) {
    if (qualities.empty()) {
        return "No Quality Available";
    }

    // Sort by required bandwidth (ascending)
    sort(qualities.begin(), qualities.end(), [](const Quality& a, const Quality& b) {
        return a.required < b.required;
    });

    string result = "No Quality Available";

    for (const auto& quality : qualities) {
        if (quality.required <= bandwidth) {
            result = quality.quality;  // Keep updating as we find better quality
        } else {
            break; // No need to check further
        }
    }

    return result;
}

int main() {
    int bandwidth;
    cin >> bandwidth;

    int n;
    cin >> n;

    vector<Quality> qualities(n);
    for (int i = 0; i < n; ++i) {
        cin >> qualities[i].quality >> qualities[i].required;
    }

    cout << selectStreamQuality(bandwidth, qualities);
    return 0;
}
```

---

## 🏷️ Tags  
`🎥 Stream Optimization` | `🔢 Sorting` | `🎯 Binary Search (Optional)` | `📶 Bandwidth Constraints` | `🎮 Greedy Selection`

---

## 👨‍💻 Author  

### 🚀 **Darshan Vasani**  
🎯 Full-Stack Developer | C++ + DSA Enthusiast | Mentor & Open Source Contributor  

### 🔗 Stay Connected  
- 🌐 [dpvasani56.vercel.app](https://dpvasani56.vercel.app)  
- 🧑‍💻 [GitHub](https://github.com/dpvasani)  
- 💼 [LinkedIn](https://linkedin.com/in/dpvasani56)  
- 🧵 [Twitter](https://x.com/vasanidarshan56)  
- 📞 [Topmate](https://topmate.io/dpvasani56)

---
