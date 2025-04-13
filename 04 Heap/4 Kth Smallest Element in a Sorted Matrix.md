# 🧩 DSA Sheet – Problem 4: Kth Smallest Element in a Sorted Matrix

## 🎯 Problem Level  
**Medium**

---

## 📚 Problem Background  

You're building a **data analysis tool** that frequently queries for specific values from massive 2D datasets. These datasets are sorted in ascending order **both row-wise and column-wise**, allowing for optimized searching.

One common task in such tools is to **efficiently locate the kth smallest element** in a matrix without flattening or sorting the entire dataset. This is crucial for performance in large-scale systems.

---

## 📝 Problem Statement  

Given:  
- A square matrix `matrix` of size `n x n` where **each row and each column is sorted in ascending order**.  
- An integer `k` (1 ≤ k ≤ n²) representing the **position** (1-indexed) of the smallest element you need to find.

Return:  
- The **kth smallest element** in the matrix (not necessarily distinct).

---

## 📥 Input Format  

- A 2D array `matrix` of size `n x n` (sorted in both rows and columns).  
- An integer `k`, such that `1 ≤ k ≤ n²`.

---

## 📤 Output Format  

- Return an **integer**, the `kth` smallest element in the matrix.

---

## 🧪 Example  

### 🔹 Example 1  

**Input**  
```
[[1, 5, 9], [10, 11, 13], [12, 13, 15]] | 8
```

**Output**  
```
13
```

**Explanation**  
Flattened and sorted array:  
```
[1, 5, 9, 10, 11, 12, 13, 13, 15]
```  
The **8th smallest** element is `13`.

---

## ⚙️ Constraints  

- `n == matrix.length == matrix[i].length`
- `1 ≤ n ≤ 300`
- `-10⁹ ≤ matrix[i][j] ≤ 10⁹`
- `All rows and columns are sorted in non-decreasing order`
- `1 ≤ k ≤ n²`

---

## 💻 C++ Solution  

```cpp
#include <iostream>
#include <vector>
#include <string>
#include <sstream>
using namespace std;

// Counts elements ≤ mid in the matrix
int countLessEqual(const vector<vector<int>>& matrix, int mid, int n) {
    int count = 0;
    int row = n - 1, col = 0;
    
    while (row >= 0 && col < n) {
        if (matrix[row][col] <= mid) {
            count += row + 1;
            col++;
        } else {
            row--;
        }
    }
    
    return count;
}

int kthSmallest(vector<vector<int>>& matrix, int k) {
    int n = matrix.size();
    int low = matrix[0][0];
    int high = matrix[n - 1][n - 1];
    
    while (low < high) {
        int mid = low + (high - low) / 2;
        int count = countLessEqual(matrix, mid, n);
        
        if (count < k)
            low = mid + 1;
        else
            high = mid;
    }
    
    return low;
}

// Please don't remove the code below
int main() {
    string input;
    getline(cin, input);
    
    try {
        // Parse input
        size_t pipePos = input.find('|');
        if (pipePos == string::npos) {
            cout << "Invalid input";
            return 0;
        }
        
        string matrixStr = input.substr(0, pipePos);
        string kStr = input.substr(pipePos + 1);
        
        // Parse k
        int k = stoi(kStr);
        
        // Parse matrix
        vector<vector<int>> matrix;
        size_t start = matrixStr.find('[');
        size_t end = matrixStr.find_last_of(']');
        
        if (start != string::npos && end != string::npos) {
            string content = matrixStr.substr(start + 1, end - start - 1);
            size_t pos = 0;
            
            while ((pos = content.find('[', pos)) != string::npos) {
                size_t endPos = content.find(']', pos);
                if (endPos != string::npos) {
                    string rowStr = content.substr(pos + 1, endPos - pos - 1);
                    vector<int> row;
                    
                    stringstream ss(rowStr);
                    string value;
                    while (getline(ss, value, ',')) {
                        row.push_back(stoi(value));
                    }
                    
                    matrix.push_back(row);
                    pos = endPos + 1;
                } else {
                    break;
                }
            }
        }
        
        // Get result
        int result = kthSmallest(matrix, k);
        
        // Output result
        cout << result;
    }
    catch (const exception&) {
        cout << "Invalid input";
    }
    
    return 0;
}
```

---

## 🏷️ Tags  
`🔢 Matrix Search` | `📊 Binary Search` | `⏱️ Efficient Search` | `📉 Sorted Matrix`

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

--- 
