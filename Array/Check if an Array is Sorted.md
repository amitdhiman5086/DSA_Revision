# Check if an Array is Sorted

## Problem Statement

Given an array of size \(n\), write a program to check if the given array is sorted in (ascending/increasing/non-decreasing) order or not. If the array is sorted, return `True`; otherwise, return `False`.

### Examples

#### Example 1

**Input:**

```plaintext
N = 5, array[] = {1, 2, 3, 4, 5}
```

**Output:**

```plaintext
True
```

**Explanation:**
The given array is sorted as every element is smaller than or equal to its next element.

#### Example 2

**Input:**

```plaintext
N = 5, array[] = {5, 4, 6, 7, 8}
```

**Output:**

```plaintext
False
```

**Explanation:**
The given array is not sorted because the first element (5) is not smaller than or equal to the next elements.

## Approaches

### Approach 1: Brute Force

**Intuition:**
Compare each element with all future elements to check if the current element is smaller than or equal to all its future elements.

**Steps:**

1. Traverse the array starting from the 0th index.
2. For each element, compare it with all future elements.
3. If any element is greater than a future element, return `False`.
4. If the entire array is traversed successfully, return `True`.

**Complexity Analysis:**

- **Time Complexity:** \(O(N^2)\) due to nested loops.
- **Space Complexity:** \(O(1)\).

**C++ Code:**

```cpp
#include <bits/stdc++.h>
using namespace std;

bool isSorted(int arr[], int n) {
    for (int i = 0; i < n; i++) {
        for (int j = i + 1; j < n; j++) {
            if (arr[j] < arr[i])
                return false;
        }
    }
    return true;
}

int main() {
    int arr[] = {1, 2, 3, 4, 5}, n = 5;
    bool ans = isSorted(arr, n);
    cout << (ans ? "True" : "False") << endl;
    return 0;
}
```

### Output:

```plaintext
True
```

### Approach 2: Optimal Approach

**Intuition:**
For a sorted array, each element must be smaller than or equal to its next element. Traverse the array once and check if each element satisfies this condition.

**Steps:**

1. Traverse the array starting from the 1st index.
2. For each element, check if it is greater than the previous element.
3. If any element is greater than the previous element, return `False`.
4. If the entire array is traversed successfully, return `True`.

**Complexity Analysis:**

- **Time Complexity:** \(O(N)\), single traversal.
- **Space Complexity:** \(O(1)\).

**C++ Code:**

```cpp
#include <bits/stdc++.h>
using namespace std;

bool isSorted(int arr[], int n) {
    for (int i = 1; i < n; i++) {
        if (arr[i] < arr[i - 1])
            return false;
    }
    return true;
}

int main() {
    int arr[] = {1, 2, 3, 4, 5}, n = 5;
    cout << (isSorted(arr, n) ? "True" : "False") << endl;
    return 0;
}
```

### Output:

```plaintext
True
```

---
