# 🚂 DSA Sheet – Problem 3: Train Seating Arrangement (a.k.a. Lone Survivor)

## 🎯 Problem Level  
**Easy**

---

## 🔍 Problem Background  

Sherlock Holmes is racing against time!  
He intercepted secret communications where **every message appears twice**, *except one* — the **Lone Survivor**.  

Your job, as his trusted assistant, is to **find the unique message** — the number that appears **only once** in the list.  

But beware:  
✅ The solution must be **fast** — **O(n)** time.  
✅ And stealthy — **O(1)** space usage.

Use your bitwise deduction powers to crack the case! 🕵️‍♂️

---

## 📝 Problem Statement  

Given an array `nums` where:  
- Every number appears **exactly twice**,  
- Except for **one number**, which appears **only once**,  

You must return the **unique number**.

---

## 📥 Input Format  

- A **vector of integers** `nums`  
- Each element appears **twice**, except **one**

---

## 📤 Output Format  

- A **single integer** — the **unique element**

---

## 🧪 Example  

### 🔹 Input  
```
[4, 1, 2, 1, 2]
```

### 🔹 Output  
```
4
```

### 🧠 Explanation  
- Every number appears twice: `1, 2`  
- The number `4` appears **only once** → it's the **Lone Survivor**

---

## ⚙️ Constraints  

- `1 <= nums.length <= 3 * 10^4`  
- `-3 * 10^4 <= nums[i] <= 3 * 10^4`  
- Exactly **one element appears once**, rest appear twice  

---

## 💡 Optimal Approach  

Use **XOR ( ^ )**:  
- `a ^ a = 0`  
- `a ^ 0 = a`  
- All duplicates cancel out, leaving only the unique one.

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <vector>
#include <sstream>
using namespace std;

// 🧠 XOR magic to find the lone survivor
int findUniqueNumber(vector<int>& nums) {
    int result = 0;
    for (int num : nums) {
        result ^= num;
    }
    return result;
}

int main() {
    string input;
    getline(cin, input);
    
    // 🔄 Parse input: remove brackets
    input = input.substr(1, input.length() - 2);
    stringstream ss(input);
    string item;
    vector<int> nums;
    
    while (getline(ss, item, ',')) {
        nums.push_back(stoi(item));
    }

    // 🕵️ Output the lone number
    cout << findUniqueNumber(nums);
    return 0;
}
```

---

## 🏷️ Tags  
`🧠 XOR` | `🧮 Bit Manipulation` | `🔁 Linear Scan` | `💾 O(1) Space`

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
