# 🧩 DSA Sheet – Problem 10: Turn The Picture

## 🎯 Problem Level  
**Easy**

---

## 📚 Problem Background  

When users upload square photos to platforms like Instagram, it's common for the photo to be in the wrong orientation. To fix this, you'll implement a feature in the profile picture editor to rotate a square photo by **90 degrees clockwise**. 

Your task is to write a function that takes in a square matrix and rotates it 90 degrees clockwise, as if rotating the image on-screen.

---

## 📝 Problem Statement  

Given:
- An integer `n`, representing the size of a square matrix.
- A 2D array (matrix) of size `n x n`, where each element represents a pixel value (an integer between 0 and 255, simulating RGB pixel values).

Your task is to rotate the matrix by 90 degrees clockwise and return the rotated matrix.

---

## 📥 Input Format  

- An integer `n` (1 <= n <= 10^3) representing the size of the matrix.
- An `n x n` matrix (2D array) where each element is an integer representing the pixel value of the image (0 <= matrix[i][j] <= 255).

---

## 📤 Output Format  

- Return the rotated matrix after rotating it 90 degrees clockwise.

---

## 🧪 Example  

### 🔹 Example 1  

**Input**  
```
3
1 2 3
4 5 6
7 8 9
```

**Output**  
```
7 4 1
8 5 2
9 6 3
```

**Explanation**  
After rotating the 3x3 matrix 90 degrees clockwise, the resulting matrix is:

```
7 4 1  
8 5 2  
9 6 3  
```

---

## ⚙️ Constraints  

- `1 ≤ n ≤ 10^3`
- `0 ≤ matrix[i][j] ≤ 255`

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

// Function to rotate the matrix 90 degrees clockwise
void rotate(vector<vector<int>>& matrix) {
    int n = matrix.size();
    
    // Step 1: Transpose the matrix
    for (int i = 0; i < n; i++) {
        for (int j = i + 1; j < n; j++) {
            swap(matrix[i][j], matrix[j][i]);
        }
    }
    
    // Step 2: Reverse each row to achieve the 90-degree clockwise rotation
    for (int i = 0; i < n; i++) {
        reverse(matrix[i].begin(), matrix[i].end());
    }
}

int main() {
    vector<vector<int>> matrix;
    int n;
    cin >> n;
    
    // Reading the matrix
    for (int i = 0; i < n; i++) {
        vector<int> row;
        for (int j = 0; j < n; j++) {
            int x;
            cin >> x;
            row.push_back(x);
        }
        matrix.push_back(row);
    }

    // Rotate the matrix
    rotate(matrix);
    
    // Print the rotated matrix
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            if (j == n - 1) {
                cout << matrix[i][j];
            } else {
                cout << matrix[i][j] << " ";
            }
        }
        if (i != n - 1) { 
            cout << endl;
        }
    }
    
    return 0;
}
```

---

## 🏷️ Tags  
`🧑‍💻 Matrix Manipulation` | `🧠 Image Rotation` | `🔧 Algorithm` | `📝 Code Optimization`

---

## 👨‍💻 Author  

### 🚀 **Darshan Vasani**  
💡 Full-Stack Developer | Mentor | DSA & System Design Enthusiast  

### 🌐 Connect with Me  
- 🌐 Website: [dpvasani56.vercel.app](https://dpvasani56.vercel.app)  
- 💼 LinkedIn: [@dpvasani56](https://linkedin.com/in/dpvasani56)  
- 🧑‍💻 GitHub: [@dpvasani](https://github.com/dpvasani)  
- 🗂️ Linktree: [linktr.ee/dpvasani56](https://linktr.ee/dpvasani56)  
- 📞 Topmate: [topmate.io/dpvasani56](https://topmate.io/dpvasani56)

