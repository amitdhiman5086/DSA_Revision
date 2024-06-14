### Insertion Sort Algorithm - Concise Notes for Revision

#### Problem Statement:
Given an array of N integers, write a program to implement the Insertion sorting algorithm.

#### Examples:

1. **Input:** `N = 6, array[] = {13, 46, 24, 52, 20, 9}`
   **Output:** `9, 13, 20, 24, 46, 52`
   **Explanation:** 
   - After sorting, the array is: `9, 13, 20, 24, 46, 52`.

2. **Input:** `N = 5, array[] = {5, 4, 3, 2, 1}`
   **Output:** `1, 2, 3, 4, 5`
   **Explanation:** 
   - After sorting, the array is: `1, 2, 3, 4, 5`.

#### Approach:

1. **Select an Element:**
   - In each iteration, select an element from the unsorted array using an outer loop.

2. **Place in Sorted Position:**
   - Move the element to its correct position in the sorted part of the array by shifting elements accordingly using an inner loop and swapping.

3. **Shifting Elements:**
   - The inner while loop shifts the elements to make space for the selected element.

#### Example Dry Run:

- **Given Array:** `{13, 46, 24, 52, 20, 9}`

  **Iteration 1:**
  - **Selected Element (i = 0):** `13`
  - **Sorted Part:** `{13}`
  - **Unsorted Part:** `{46, 24, 52, 20, 9}`

  **Iteration 2:**
  - **Selected Element (i = 1):** `46`
  - **Sorted Part:** `{13, 46}`
  - **Unsorted Part:** `{24, 52, 20, 9}`
  - - `46` is already in the correct position.

  **Iteration 3:**
  - **Selected Element (i = 2):** `24`
  - **Sorted Part:** `{13, 24, 46}`
  - **Unsorted Part:** `{52, 20, 9}`
  - - `24` is placed between `13` and `46` by swapping.

  **Iteration 4:**
  - **Selected Element (i = 3):** `52`
  - **Sorted Part:** `{13, 24, 46, 52}`
  - **Unsorted Part:** `{20, 9}`
  - - `52` is already in the correct position.

  **Iteration 5:**
  - **Selected Element (i = 4):** `20`
  - **Sorted Part:** `{13, 20, 24, 46, 52}`
  - **Unsorted Part:** `{9}`
  - - `20` is placed between `13` and `24` by swapping adjacent elements.

  **Iteration 6:**
  - **Selected Element (i = 5):** `9`
  - **Sorted Part:** `{9, 13, 20, 24, 46, 52}`
  - **Unsorted Part:** `{}` (Array is sorted)
  - - `9` is placed at the start of the array by multiple swaps.

- **Sorted Array:** `{9, 13, 20, 24, 46, 52}`

#### Code Implementation:

```cpp
#include <bits/stdc++.h>
using namespace std;

void insertion_sort(int arr[], int n) {
    for (int i = 0; i <= n - 1; i++) {
        int j = i;
        while (j > 0 && arr[j - 1] > arr[j]) {
            int temp = arr[j - 1];
            arr[j - 1] = arr[j];
            arr[j] = temp;
            j--;
        }
    }

    cout << "After Using insertion sort: " << "\n";
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << "\n";
}

int main() {
    int arr[] = {13, 46, 24, 52, 20, 9};
    int n = sizeof(arr) / sizeof(arr[0]);
    cout << "Before Using insertion Sort: " << endl;
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    insertion_sort(arr, n);
    return 0;
}
```

**Output:**
```
Before insertion sort:
13 46 24 52 20 9
After insertion sort:
9 13 20 24 46 52
```

#### Complexity Analysis:

- **Time Complexity:** \(O(N^2)\) for the worst and average cases.
  - The outer loop runs `N` times.
  - The inner loop runs from `i` to `1`, approximately summing up to the first `N` natural numbers, resulting in a total of \(\frac{N(N-1)}{2}\) comparisons.

- **Space Complexity:** `O(1)` (in-place sorting).

- **Best Case Time Complexity:** \(O(N)\)
  - Occurs when the array is already sorted. The inner loop does not run, so the overall complexity is linear.

#### Use Cases:

1. **When to Use:**
   - Small datasets where simplicity and ease of implementation are desired.
   - When the array is nearly sorted, as the algorithm is efficient for such cases.

2. **When Not to Use:**
   - Large datasets due to its \(O(N^2)\) time complexity, which makes it inefficient compared to more advanced sorting algorithms like Quick Sort or Merge Sort.

3. **Examples of Use:**
   - Sorting a small list of integers.
   - Organizing a nearly sorted list, such as adding a few new elements to an already sorted array.

4. **Comparison with Other Algorithms:**
   - **Selection Sort:** Performs fewer swaps but has the same time complexity.
   - **Bubble Sort:** Generally slower due to more swaps.
   - **Quick Sort:** Much faster for large datasets but not stable; Insertion Sort is stable and more predictable for small or nearly sorted datasets.
