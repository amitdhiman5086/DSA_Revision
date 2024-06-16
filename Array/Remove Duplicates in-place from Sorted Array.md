# Remove Duplicates In-Place from Sorted Array

## Problem Statement

Given an integer array sorted in non-decreasing order, remove the duplicates in place such that each unique element appears only once. The relative order of the elements should be kept the same.

If there are \( k \) elements after removing the duplicates, then the first \( k \) elements of the array should hold the final result. It does not matter what you leave beyond the first \( k \) elements.

Note: Return \( k \) after placing the final result in the first \( k \) slots of the array.

## Examples

### Example 1

**Input:**

```plaintext
arr = [1, 1, 2, 2, 2, 3, 3]
```

**Output:**

```plaintext
arr = [1, 2, 3, _, _, _, _]
```

**Explanation:**
Total number of unique elements is 3, i.e., [1, 2, 3]. Therefore, return 3 after assigning [1, 2, 3] in the beginning of the array.

### Example 2

**Input:**

```plaintext
arr = [1, 1, 1, 2, 2, 3, 3, 3, 3, 4, 4]
```

**Output:**

```plaintext
arr = [1, 2, 3, 4, _, _, _, _, _, _, _]
```

**Explanation:**
Total number of unique elements is 4, i.e., [1, 2, 3, 4]. Therefore, return 4 after assigning [1, 2, 3, 4] in the beginning of the array.

## Approaches

### Approach 1: Brute Force

**Intuition:**
Use a data structure that does not store duplicate elements, like a hash set. HashSet only stores unique elements.

**Steps:**

1. Declare a HashSet.
2. Run a for loop from start to end of the array.
3. Insert each element of the array into the set.
4. Store the size of the set in a variable \( k \).
5. Place all elements of the set back into the array starting from the beginning.
6. Return \( k \).

**Complexity Analysis:**

- **Time Complexity:** \( O(N \log N) + O(N) \)
- **Space Complexity:** \( O(N) \)

**C++ Code:**

```cpp
#include <bits/stdc++.h>
using namespace std;

int removeDuplicates(int arr[], int n) {
    set<int> s;
    for (int i = 0; i < n; i++) {
        s.insert(arr[i]);
    }
    int k = s.size();
    int j = 0;
    for (int x : s) {
        arr[j++] = x;
    }
    return k;
}

int main() {
    int arr[] = {1, 1, 2, 2, 2, 3, 3};
    int n = sizeof(arr) / sizeof(arr[0]);
    int k = removeDuplicates(arr, n);
    cout << "The array after removing duplicate elements is: " << endl;
    for (int i = 0; i < k; i++) {
        cout << arr[i] << " ";
    }
    return 0;
}
```

**Output:**

```plaintext
The array after removing duplicate elements is: 1 2 3
```

### Approach 2: Two Pointers

**Intuition:**
Use two pointers, `i` and `j`. Move `j` until we find a number different from `arr[i]`. When we find such a number, increase `i` and update `arr[i]` to `arr[j]`.

**Steps:**

1. Initialize a variable `i` to 0.
2. Use a for loop with variable `j` from 1 to the length of the array.
3. If `arr[j]` is not equal to `arr[i]`, increment `i` and update `arr[i]` to `arr[j]`.
4. After the loop completes, return `i + 1` as the size of the array of unique elements.

**Complexity Analysis:**

- **Time Complexity:** \( O(N) \)
- **Space Complexity:** \( O(1) \)

**C++ Code:**

```cpp
#include <bits/stdc++.h>
using namespace std;

int removeDuplicates(int arr[], int n) {
    if (n == 0) return 0;
    int i = 0;
    for (int j = 1; j < n; j++) {
        if (arr[i] != arr[j]) {
            i++;
            arr[i] = arr[j];
        }
    }
    return i + 1;
}

int main() {
    int arr[] = {1, 1, 2, 2, 2, 3, 3};
    int n = sizeof(arr) / sizeof(arr[0]);
    int k = removeDuplicates(arr, n);
    cout << "The array after removing duplicate elements is: " << endl;
    for (int i = 0; i < k; i++) {
        cout << arr[i] << " ";
    }
    return 0;
}
```

**Output:**

```plaintext
The array after removing duplicate elements is: 1 2 3
```

---

These approaches provide two different methods to solve the problem of removing duplicates from a sorted array in-place. The first uses a set for simplicity, while the second employs a more efficient two-pointer technique.
