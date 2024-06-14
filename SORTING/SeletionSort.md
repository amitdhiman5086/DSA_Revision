

## Selection Sort Algorithm - Concise Notes for Revision

### Problem Statement:
Given an array of N integers, sort it using the Selection Sort algorithm.

### Examples:
1. **Input:** `N = 6, array[] = {13, 46, 24, 52, 20, 9}`
   - **Output:** `9, 13, 20, 24, 46, 52`

2. **Input:** `N = 5, array[] = {5, 4, 3, 2, 1}`
   - **Output:** `1, 2, 3, 4, 5`

### Approach:

1. **Initialize the Range:**
   - Loop from `0` to `N-1` (`i` is the current starting index).
   - Initially, the range is the entire array.

2. **Find Minimum Element:**
   - Use an inner loop to find the minimum element in the unsorted part of the array (from index `i` to `N-1`).

3. **Swap Elements:**
   - Swap the minimum element found with the first element of the current range.

4. **Repeat Until Sorted:**
   - After each iteration, the array is sorted up to the first index of the range.
   - Increment the starting index for the next iteration.

### Example Dry Run:
- **Given Array:** `{7, 5, 9, 2, 8}`

  **Iteration 1:**
  - **Range:** `{7, 5, 9, 2, 8}`
  - **Minimum:** `2`
  - **Swap:** `{2, 5, 9, 7, 8}`

  **Iteration 2:**
  - **Range:** `{5, 9, 7, 8}`
  - **Minimum:** `5`
  - **Swap:** `{2, 5, 9, 7, 8}`

  **Iteration 3:**
  - **Range:** `{9, 7, 8}`
  - **Minimum:** `7`
  - **Swap:** `{2, 5, 7, 9, 8}`

  **Iteration 4:**
  - **Range:** `{9, 8}`
  - **Minimum:** `8`
  - **Swap:** `{2, 5, 7, 8, 9}`

- **Sorted Array:** `{2, 5, 7, 8, 9}`

### Code Implementation:

```cpp
#include<bits/stdc++.h>
using namespace std;

void selection_sort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {
        int mini = i;
        for (int j = i + 1; j < n; j++) {
            if (arr[j] < arr[mini]) {
                mini = j;
            }
        }
        swap(arr[mini], arr[i]);
    }

    cout << "After selection sort: " << "\n";
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << "\n";
}

int main() {
    int arr[] = {13, 46, 24, 52, 20, 9};
    int n = sizeof(arr) / sizeof(arr[0]);
    cout << "Before selection sort: " << "\n";
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << "\n";
    selection_sort(arr, n);
    return 0;
}
```

**Output:**
```
Before selection sort:
13 46 24 52 20 9
After selection sort:
9 13 20 24 46 52
```

### Complexity Analysis:

- **Time Complexity:** `O(N^2)` for best, worst, and average cases.
  - The outer loop runs `N-1` times.
  - The inner loop runs from `i` to `N-1`, leading to a total of `((N-1(N))/2)` comparisons.

- **Space Complexity:** `O(1)` (in-place sorting).

### Use Cases:

1. **When to Use:**
   - Small datasets where simplicity is preferred over efficiency.
   - When memory usage needs to be minimal since Selection Sort is in-place.

2. **When Not to Use:**
   - Large datasets due to its `O(N^2)` time complexity, which is inefficient compared to other sorting algorithms like Merge Sort or Quick Sort.

3. **Examples of Use:**
   - Sorting a small list of names alphabetically.
   - Ordering a short sequence of numbers in a particular order.

4. **Comparison with Other Algorithms:**
   - **Bubble Sort:** Similar time complexity but generally slower due to more swaps.
   - **Insertion Sort:** Faster for nearly sorted arrays, but Selection Sort always makes `N` swaps regardless of the initial order.
   - **Quick Sort:** Much faster for large datasets but not stable; Selection Sort is more predictable but slowe
