# Finding the Largest Element in an Array

## Problem Statement

Given an array, we need to find the largest element in the array.

### Examples

#### Example 1

**Input:**

```plaintext
arr[] = {2, 5, 1, 3, 0}
```

**Output:**

```plaintext
5
```

**Explanation:**
5 is the largest element in the array.

#### Example 2

**Input:**

```plaintext
arr[] = {8, 10, 5, 7, 9}
```

**Output:**

```plaintext
10
```

**Explanation:**
10 is the largest element in the array.

## Approach

### Intuition

We can maintain a `max_element` variable that will update whenever the current value is greater than the value in the `max_element` variable.

### Steps

1. Initialize a variable `max_element` with the first element of the array.
2. Iterate through each element of the array.
3. If the current element is greater than `max_element`, update `max_element` with the current element.
4. After completing the iteration, `max_element` will hold the largest element of the array.

### Complexity Analysis

- **Time Complexity:** \(O(N)\), where \(N\) is the number of elements in the array. This is because we only need to traverse the array once.
- **Space Complexity:** \(O(1)\), as we are using only a constant amount of extra space.

## C++ Implementation

```cpp
#include <iostream>
using namespace std;

int findLargestElement(int arr[], int n) {
    // Initialize max with the first element of the array
    int max_element = arr[0];

    // Iterate through the array
    for (int i = 1; i < n; i++) {
        if (arr[i] > max_element) {
            max_element = arr[i];
        }
    }

    return max_element;
}

int main() {
    int arr1[] = {2, 5, 1, 3, 0};
    int n1 = sizeof(arr1) / sizeof(arr1[0]);
    cout << "The largest element in the array is: " << findLargestElement(arr1, n1) << endl;

    int arr2[] = {8, 10, 5, 7, 9};
    int n2 = sizeof(arr2) / sizeof(arr2[0]);
    cout << "The largest element in the array is: " << findLargestElement(arr2, n2) << endl;

    return 0;
}
```

### Output

The output of the above code will be:

```plaintext
The largest element in the array is: 5
The largest element in the array is: 10
```

This approach ensures that we find the largest element efficiently without unnecessary sorting or additional space usage.

---
