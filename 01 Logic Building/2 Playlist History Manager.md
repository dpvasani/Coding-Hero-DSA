# 🎵 DSA Sheet – Problem 2: Playlist History Manager
## 🎯 Problem Level  
**Easy**

---


## 🛡️ Problem Background  

You are building a **playlist system** for a **music app**. Users can **add songs** to their playlist and **undo** their last action if they make a mistake.  

Your task is to implement this functionality using a **stack** data structure.  

The **undo** feature will remove the **last song added**, and there’s **no redo** functionality for now.

---

## 📜 Problem Statement  

Write a function to **simulate** adding songs and **undoing the last action** in a playlist manager. The function should **process a series of actions** and return the final **state of the playlist**.

### ✅ Supported Actions  

1️⃣ `addSong('Song Name')` → Add a song to the playlist  
2️⃣ `undo()` → Remove the most recently added song  

---

## 📝 Input Format  

📌 A **list of strings** `actions`, where each string is an action:  
- `1 <= number of actions <= 100`  

✅ All actions will be **valid**. `undo()` will only appear if there's at least one song in the playlist.

## 🎯 Output Format  

🔹 A **list of strings** representing the **final playlist**

---

## 📌 Example  

### 🔹 Input  
```cpp
["addSong('Song 1')", "addSong('Song 2')", "undo()", "addSong('Song 3')"]
```

### 🔹 Output  
```cpp
["Song 1", "Song 3"]
```

### 🧐 Explanation  
✔️ Action 1: Add `"Song 1"` → Playlist: `["Song 1"]`  
✔️ Action 2: Add `"Song 2"` → Playlist: `["Song 1", "Song 2"]`  
✔️ Action 3: Undo last → Remove `"Song 2"` → Playlist: `["Song 1"]`  
✔️ Action 4: Add `"Song 3"` → Playlist: `["Song 1", "Song 3"]`  

---

## ⚡ Constraints  

- `1 <= number of actions <= 100`  
- All actions are **guaranteed to be valid**  

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <vector>
#include <sstream>
#include <string>
using namespace std;

vector<string> playlistManager(const vector<string>& actions) {
    vector<string> playlist;

    for (const string& action : actions) {
        if (action.find("addSong") == 0) {
            size_t start = action.find('\'') + 1;
            size_t end = action.rfind('\'');
            string song = action.substr(start, end - start);
            playlist.push_back(song);
        } else if (action == "undo()") {
            if (!playlist.empty()) {
                playlist.pop_back();
            }
        }
    }

    return playlist;
}

// Please don't remove the code below
int main() {
    string input;
    getline(cin, input);

    vector<string> actions;
    string action;
    stringstream ss(input.substr(1, input.size() - 2)); // Remove brackets

    while (getline(ss, action, ',')) {
        actions.push_back(action.substr(action.find('"') + 1, action.rfind('"') - action.find('"') - 1));
    }

    vector<string> result = playlistManager(actions);

    cout << "[";
    for (size_t i = 0; i < result.size(); ++i) {
        cout << "\"" << result[i] << "\"";
        if (i != result.size() - 1) cout << ", ";
    }
    cout << "]";
    return 0;
}
```

---

## 🏷️ Tags  

`🎵 Stack` | `📚 Simulation` | `🔁 Undo Operation` | `🧠 String Parsing`  

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
