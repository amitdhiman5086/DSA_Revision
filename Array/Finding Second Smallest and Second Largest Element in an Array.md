# Finding Second Smallest and Second Largest Element in an Array

## Problem Statement

Given an array, find the second smallest and second largest element in the array. Print ‘-1’ if either of them doesn’t exist.

### Examples

#### Example 1

**Input:**

```plaintext
[1, 2, 4, 7, 7, 5]
```

**Output:**

```plaintext
Second Smallest: 2
Second Largest: 5
```

**Explanation:**
The elements are 1, 2, 3, 5, 7, 7 and hence the second largest is 5 and the second smallest is 2.

#### Example 2

**Input:**

```plaintext
[1]
```

**Output:**

```plaintext
Second Smallest: -1
Second Largest: -1
```

**Explanation:**
Since there is only one element in the array, there is no second largest or second smallest element.

## Approaches

### Approach 1: Brute Force

**Intuition:**
Sort the array and then find the second smallest and second largest elements based on their positions.

**Steps:**

1. Sort the array in ascending order.
2. The element at index 1 (second position) is the second smallest.
3. The element at index `n-2` (second last position) is the second largest.

**Complexity Analysis:**

- **Time Complexity:** \(O(N \log N)\) due to sorting.
- **Space Complexity:** \(O(1)\).

**C++ Code:**

```cpp
#include<bits/stdc++.h>
using namespace std;

void getElements(int arr[], int n) {
    if (n < 2) {
        cout << -1 << " " << -1 << endl;  // Edge case: less than 2 elements
        return;
    }
    sort(arr, arr + n);
    int small = arr[1];
    int large = arr[n - 2];
    cout << "Second smallest is " << small << endl;
    cout << "Second largest is " << large << endl;
}

int main() {
    int arr[] = {1, 2, 4, 6, 7, 5};
    int n = sizeof(arr) / sizeof(arr[0]);
    getElements(arr, n);
    return 0;
}
```

### Output:

```plaintext
Second smallest is 2
Second largest is 6
```

### Approach 2: Two Pass Solution

**Intuition:**
Find the smallest and largest element in one pass, then find the second smallest and second largest in another pass.

**Steps:**

1. Traverse the array to find the smallest and largest elements.
2. Traverse the array again to find the second smallest (greater than the smallest) and second largest (less than the largest) elements.

**Complexity Analysis:**

- **Time Complexity:** \(O(N)\), two traversals.
- **Space Complexity:** \(O(1)\).

**C++ Code:**

```cpp
#include<bits/stdc++.h>
using namespace std;

void getElements(int arr[], int n) {
    if (n < 2) {
        cout << -1 << " " << -1 << endl;  // Edge case: less than 2 elements
        return;
    }
    int small = INT_MAX, second_small = INT_MAX;
    int large = INT_MIN, second_large = INT_MIN;

    for (int i = 0; i < n; i++) {
        small = min(small, arr[i]);
        large = max(large, arr[i]);
    }

    for (int i = 0; i < n; i++) {
        if (arr[i] < second_small && arr[i] != small)
            second_small = arr[i];
        if (arr[i] > second_large && arr[i] != large)
            second_large = arr[i];
    }

    cout << "Second smallest is " << second_small << endl;
    cout << "Second largest is " << second_large << endl;
}

int main() {
    int arr[] = {1, 2, 4, 6, 7, 5};
    int n = sizeof(arr) / sizeof(arr[0]);
    getElements(arr, n);
    return 0;
}
```

### Output:

```plaintext
Second smallest is 2
Second largest is 6
```

### Approach 3: Single Pass Solution

**Intuition:**
Use four variables (`small`, `second_small`, `large`, `second_large`) to keep track of the smallest, second smallest, largest, and second largest elements during a single traversal.

**Steps:**

1. Initialize `small` and `second_small` to `INT_MAX`.
2. Initialize `large` and `second_large` to `INT_MIN`.
3. Traverse the array and update these variables accordingly.

**Complexity Analysis:**

- **Time Complexity:** \(O(N)\), single traversal.
- **Space Complexity:** \(O(1)\).

**C++ Code:**

```cpp
#include<bits/stdc++.h>
using namespace std;

int secondSmallest(int arr[], int n) {
    if (n < 2)
        return -1;
    int small = INT_MAX;
    int second_small = INT_MAX;

    for (int i = 0; i < n; i++) {
        if (arr[i] < small) {
            second_small = small;
            small = arr[i];
        } else if (arr[i] < second_small && arr[i] != small) {
            second_small = arr[i];
        }
    }
    return second_small;
}

int secondLargest(int arr[], int n) {
    if (n < 2)
        return -1;
    int large = INT_MIN;
    int second_large = INT_MIN;

    for (int i = 0; i < n; i++) {
        if (arr[i] > large) {
            second_large = large;
            large = arr[i];
        } else if (arr[i] > second_large && arr[i] != large) {
            second_large = arr[i];
        }
    }
    return second_large;
}

int main() {
    int arr[] = {1, 2, 4, 7, 7, 5};
    int n = sizeof(arr) / sizeof(arr[0]);
    int sS = secondSmallest(arr, n);
    int sL = secondLargest(arr, n);
    cout << "Second smallest is " << sS << endl;
    cout << "Second largest is " << sL << endl;
    return 0;
}
```

### Output:

```plaintext
Second smallest is 2
Second largest is 5
```

---
