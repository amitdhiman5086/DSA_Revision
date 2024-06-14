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



## Recursive Insertion Sort Algorithm - Detailed Overview

---

#### Problem Statement:

Given an array of N integers, write a program to implement the Recursive Insertion Sort algorithm.

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

1. **Iterative Insertion Sort Recap:**
   - **Step 1:** Take an element from the unsorted part.
   - **Step 2:** Place it in the correct position in the sorted part.
   - **Step 3:** Shift the remaining elements accordingly.

2. **Recursive Approach:**
   - The key difference is using recursion instead of loops to handle the sorting.
   - **Steps:**
     - Call the recursive function with the array and the current index.
     - Take the current element and place it in the sorted portion.
     - Call the recursive function for the next index.
     - Continue until the entire array is sorted.

3. **Dry Run:**
   - **Recursion 1:** Element at index 0 is placed correctly.
   - **Recursion 2:** Element at index 1 is placed correctly.
   - **Recursion 3:** Continue until all elements are sorted.

4. **Base Case:** The recursion stops when the index reaches the array size (i.e., all elements are sorted).

#### Code Implementation:

**C++ Code:**

```cpp
#include <bits/stdc++.h>
using namespace std;

void insertion_sort(int arr[], int i, int n) {
    // Base Case: If index reaches the size of the array.
    if (i == n) return;

    int j = i;
    // Insert arr[i] in sorted part.
    while (j > 0 && arr[j - 1] > arr[j]) {
        swap(arr[j], arr[j - 1]);
        j--;
    }

    // Recursive call for the next element.
    insertion_sort(arr, i + 1, n);
}

int main() {
    int arr[] = {13, 46, 24, 52, 20, 9};
    int n = sizeof(arr) / sizeof(arr[0]);
    cout << "Before Using Insertion Sort: " << endl;
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    insertion_sort(arr, 0, n);
    cout << "After Using Insertion Sort: " << "\n";
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << "\n";
    return 0;
}
```

**Output:**
```
Before Using Insertion Sort:
13 46 24 52 20 9
After Using Insertion Sort:
9 13 20 24 46 52
```

#### Complexity Analysis:

1. **Time Complexity:**
   - **Worst and Average Case:** \(O(N^2)\)
     - Recursion occurs `N` times, and for each call, the inner loop runs from `i` to 1, where `i` is the current index.
     - Total operations sum up to: \(1 + 2 + 3 + \ldots + (N-1)\), which is \(\frac{N(N-1)}{2}\), simplifying to \(O(N^2)\).
   - **Best Case:** \(O(N)\)
     - If the array is already sorted, each recursive call completes in constant time \(O(1)\), as no swaps are needed.

2. **Space Complexity:**
   - **Auxiliary Stack Space:** \(O(N)\)
     - Each recursive call adds to the call stack, and with `N` elements, we have `N` recursive calls.

#### Optimized Approach:

To optimize for the best case (already sorted array), we can add a check to skip unnecessary recursive calls if the current sub-array is already sorted.

**C++ Code with Optimization:**

```cpp
#include <bits/stdc++.h>
using namespace std;

void insertion_sort(int arr[], int i, int n) {
    // Base Case
    if (i == n) return;

    int j = i;
    bool sorted = true;
    while (j > 0 && arr[j - 1] > arr[j]) {
        swap(arr[j], arr[j - 1]);
        j--;
        sorted = false;
    }

    // If no swaps happened, the array is sorted.
    if (sorted) return;

    insertion_sort(arr, i + 1, n);
}

int main() {
    int arr[] = {13, 46, 24, 52, 20, 9};
    int n = sizeof(arr) / sizeof(arr[0]);
    cout << "Before Using Insertion Sort: " << endl;
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    insertion_sort(arr, 0, n);
    cout << "After Using Insertion Sort: " << "\n";
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << "\n";
    return 0;
}
```

#### Summary:

1. **When to Use:**
   - Best for small datasets where simplicity and recursion are preferred.
   - Educational purposes to illustrate recursive problem-solving.

2. **When Not to Use:**
   - Large datasets due to higher time complexity.
   - Scenarios where performance is critical.

3. **Comparison with Other Algorithms:**
   - **Recursive Insertion Sort vs Iterative Insertion Sort:** Both have similar time complexities; the recursive version uses more stack space.
   - **Recursive Insertion Sort vs Quick Sort:** Quick sort is faster for larger datasets, with an average complexity of \(O(N \log N)\).
   - **Recursive Insertion Sort vs Merge Sort:** Merge sort is more efficient for large datasets, with a guaranteed time complexity of \(O(N \log N)\).

This detailed overview provides a comprehensive understanding of the Recursive Insertion Sort algorithm, highlighting its process, implementation, and practical applications.