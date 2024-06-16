# Left Rotate the Array by One

## Problem Statement

Given an array of \( N \) integers, left rotate the array by one place.

## Examples

### Example 1

**Input:**

```plaintext
N = 5, array = [1, 2, 3, 4, 5]
```

**Output:**

```plaintext
[2, 3, 4, 5, 1]
```

**Explanation:**
Since all the elements in the array are shifted toward the left by one, `2` becomes the first element and `1`, which was at the first index, is shifted to the last.

### Example 2

**Input:**

```plaintext
N = 1, array = [3]
```

**Output:**

```plaintext
[3]
```

**Explanation:**
Here only one element is present, so the element remains at the first index even after rotation.

## Approaches

### Approach 1: Brute Force

**Intuition:**
The rotated array has its first element at the last index. We can use a dummy array to shift all elements to the left and place the first element at the last index.

**Steps:**

1. Create a temporary array of the same length.
2. Copy elements from the original array to the temporary array, shifting each element one position to the left.
3. Place the first element of the original array at the last position of the temporary array.
4. Print or return the temporary array.

**Complexity Analysis:**

- **Time Complexity:** \( O(N) \)
- **Space Complexity:** \( O(N) \)

**C++ Code:**

```cpp
#include <bits/stdc++.h>
using namespace std;

void solve(int arr[], int n) {
    int temp[n];
    for (int i = 1; i < n; i++) {
        temp[i - 1] = arr[i];
    }
    temp[n - 1] = arr[0];
    for (int i = 0; i < n; i++) {
        cout << temp[i] << " ";
    }
    cout << endl;
}

int main() {
    int n = 5;
    int arr[] = {1, 2, 3, 4, 5};
    solve(arr, n);
    return 0;
}
```

**Output:**

```plaintext
2 3 4 5 1
```

### Approach 2: Optimal Approach

**Intuition:**
We can achieve the left rotation in place by storing the first element in a temporary variable, shifting all other elements to the left, and then placing the first element at the last index.

**Steps:**

1. Store the first element in a temporary variable.
2. Shift all elements of the array one position to the left.
3. Place the temporary variable's value at the last index of the array.
4. Print or return the modified array.

**Complexity Analysis:**

- **Time Complexity:** \( O(N) \)
- **Space Complexity:** \( O(1) \)

**C++ Code:**

```cpp
#include <bits/stdc++.h>
using namespace std;

void solve(int arr[], int n) {
    int temp = arr[0]; // Store the first element
    for (int i = 0; i < n - 1; i++) {
        arr[i] = arr[i + 1]; // Shift elements to the left
    }
    arr[n - 1] = temp; // Place the first element at the last index
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
}

int main() {
    int n = 5;
    int arr[] = {1, 2, 3, 4, 5};
    solve(arr, n);
    return 0;
}
```

**Output:**

```plaintext
2 3 4 5 1
```

---

These approaches provide two different methods to solve the problem of left rotating an array by one place. The first uses an auxiliary array for simplicity, while the second employs an in-place technique for optimal space efficiency.
