
## Bubble Sort Algorithm - Concise Notes for Revision

### Problem Statement:
Given an array of N integers, sort it using the Bubble Sort algorithm.

### Examples:
1. **Input:** `N = 6, array[] = {13, 46, 24, 52, 20, 9}`
   - **Output:** `9, 13, 20, 24, 46, 52`

2. **Input:** `N = 5, array[] = {5, 4, 3, 2, 1}`
   - **Output:** `1, 2, 3, 4, 5`

### Approach:

1. **Select the Range:**
   - Loop from `N-1` to `0` (`i` is the last index of the range).
   - The range starts from the whole array and shrinks with each iteration.

2. **Push Maximum Element to End:**
   - Use an inner loop to compare adjacent elements and swap them if they are in the wrong order.
   - This pushes the largest element of the unsorted part to the end of the range.

3. **Repeat Until Sorted:**
   - After each iteration, the last element of the current range is in its correct position.
   - Continue this process until the array is sorted.

### Example Dry Run:
- **Given Array:** `{7, 5, 9, 2, 8}`

  **Iteration 1:**
  - **Range:** `{7, 5, 9, 2, 8}`
  - **Process:** Compare and swap adjacent elements.
  - **Result:** `{5, 7, 2, 8, 9}`

  **Iteration 2:**
  - **Range:** `{5, 7, 2, 8}`
  - **Process:** Compare and swap adjacent elements.
  - **Result:** `{5, 2, 7, 8, 9}`

  **Iteration 3:**
  - **Range:** `{5, 2, 7}`
  - **Process:** Compare and swap adjacent elements.
  - **Result:** `{2, 5, 7, 8, 9}`

  **Iteration 4:**
  - **Range:** `{2, 5}`
  - **Process:** Compare and swap adjacent elements.
  - **Result:** `{2, 5, 7, 8, 9}`

- **Sorted Array:** `{2, 5, 7, 8, 9}`

### Code Implementation:

```cpp
#include <bits/stdc++.h>
using namespace std;

void bubble_sort(int arr[], int n) {
    for (int i = n - 1; i >= 0; i--) {
        for (int j = 0; j <= i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                int temp = arr[j + 1];
                arr[j + 1] = arr[j];
                arr[j] = temp;
            }
        }
    }

    cout << "After Using bubble sort: " << "\n";
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << "\n";
}

int main() {
    int arr[] = {13, 46, 24, 52, 20, 9};
    int n = sizeof(arr) / sizeof(arr[0]);
    cout << "Before Using Bubble Sort: " << endl;
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    bubble_sort(arr, n);
    return 0;
}
```

**Output:**
```
Before Using Bubble Sort:
13 46 24 52 20 9
After Using bubble sort:
9 13 20 24 46 52
```

### Complexity Analysis:

- **Time Complexity:**
  - **Worst and Average Case:** \(O(N^2)\)
    - The outer loop runs `N` times.
    - The inner loop makes a total of \(\frac{N(N-1)}{2}\) comparisons.
  - **Best Case:** \(O(N)\)
    - If the array is already sorted, the inner loop will not perform any swaps, and the algorithm terminates early.

- **Space Complexity:** `O(1)` (in-place sorting).

### Use Cases:

1. **When to Use:**
   - Small datasets where a simple sorting method is sufficient.
   - When the overhead of more complex sorting algorithms is not justified.

2. **When Not to Use:**
   - Large datasets due to its inefficiency with \(O(N^2)\) time complexity.
   - When a faster sorting method like Quick Sort or Merge Sort is available.

3. **Examples of Use:**
   - Sorting a small list of numbers in ascending or descending order.
   - Educational purposes to demonstrate basic sorting concepts.

4. **Comparison with Other Algorithms:**
   - **Selection Sort:** Similar time complexity but Bubble Sort may perform fewer swaps.
   - **Insertion Sort:** More efficient for nearly sorted arrays.
   - **Quick Sort:** Much faster for large datasets, but more complex to implement.

### Optimized Approach:

- **Optimized Bubble Sort:** Reduce time complexity for the best case by checking if any swaps are made during an iteration. If no swaps occur, the array is already sorted.

  ```cpp
  #include <bits/stdc++.h>
  using namespace std;

  void bubble_sort(int arr[], int n) {
      for (int i = n - 1; i >= 0; i--) {
          int didSwap = 0;
          for (int j = 0; j <= i - 1; j++) {
              if (arr[j] > arr[j + 1]) {
                  int temp = arr[j + 1];
                  arr[j + 1] = arr[j];
                  arr[j] = temp;
                  didSwap = 1;
              }
          }
          if (didSwap == 0) {
              break;
          }
      }

      cout << "After Using bubble sort: " << "\n";
      for (int i = 0; i < n; i++) {
          cout << arr[i] << " ";
      }
      cout << "\n";
  }

  int main() {
      int arr[] = {13, 46, 24, 52, 20, 9};
      int n = sizeof(arr) / sizeof(arr[0]);
      cout << "Before Using Bubble Sort: " << endl;
      for (int i = 0; i < n; i++) {
          cout << arr[i] << " ";
      }
      cout << endl;

      bubble_sort(arr, n);
      return 0;
  }
  ```

**Output:**
```
Before Using Bubble Sort:
13 46 24 52 20 9
After Using bubble sort:
9 13 20 24 46 52
```


##### Recursive Bubble Sort Algorithm - Summary for Revision

---

#### Problem Statement:
Given an array of N integers, write a program to implement the Recursive Bubble Sort algorithm.

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

1. **Base Concept:**
   - The recursive bubble sort algorithm works similarly to the iterative bubble sort but uses recursion to sort the array.

2. **Step-by-Step Process:**
   - **Step 1:** Call the recursive function with the array and its size.
   - **Step 2:** Within the function, swap adjacent elements if they are in the wrong order (`arr[j] > arr[j+1]`).
   - **Step 3:** The largest unsorted element "bubbles up" to the end of the array after each recursive call.
   - **Step 4:** Recursively call the function with a reduced range, decreasing by one each time.
   - **Step 5:** The recursion stops when the range of the array reduces to 1 (base case).

3. **Dry Run:**
   - **Initial Array:** `{13, 46, 24, 52, 20, 9}`
     - **Recursion 1:** Sort array from index 0 to 5.
     - **Recursion 2:** Sort array from index 0 to 4.
     - **Recursion 3:** Sort array from index 0 to 3.
     - **Recursion 4:** Sort array from index 0 to 2.
     - **Recursion 5:** Sort array from index 0 to 1.
     - **Recursion 6:** Base case reached, array is sorted.

#### Code Implementation:

```cpp
#include <bits/stdc++.h>
using namespace std;

void bubble_sort(int arr[], int n) {
    // Base Case: range == 1.
    if (n == 1) return;

    int didSwap = 0;  // Flag to check if swapping happens
    for (int j = 0; j <= n - 2; j++) {
        if (arr[j] > arr[j + 1]) {
            int temp = arr[j + 1];
            arr[j + 1] = arr[j];
            arr[j] = temp;
            didSwap = 1;  // Swap happened
        }
    }

    // If no swapping happened, array is sorted.
    if (didSwap == 0) return;

    // Range reduced after recursion:
    bubble_sort(arr, n - 1);
}

int main() {
    int arr[] = {13, 46, 24, 52, 20, 9};
    int n = sizeof(arr) / sizeof(arr[0]);
    cout << "Before Using Bubble Sort: " << endl;
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    bubble_sort(arr, n);
    cout << "After Using Bubble Sort: " << "\n";
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << "\n";
    return 0;
}
```

**Output:**
```
Before Using Bubble Sort:
13 46 24 52 20 9
After Using Bubble Sort:
9 13 20 24 46 52
```

#### Complexity Analysis:

1. **Time Complexity:**
   - **Worst and Average Case:** \(O(N^2)\)
     - The recursion runs `N` times, and for each call, the loop runs `N-1`, `N-2`, ..., `1` times.
     - Total steps: Sum of the first `N` natural numbers: \(\frac{N(N+1)}{2}\).
   - **Best Case:** \(O(N)\)
     - If the array is already sorted, only one pass is required to confirm this.

2. **Space Complexity:**
   - **Auxiliary Stack Space:** \(O(N)\)
     - Each recursive call adds to the call stack.

3. **Optimized Approach for Best Case:**
   - Add a check to see if any swaps occurred. If not, the array is already sorted and recursion stops.

#### Use Cases:

1. **When to Use:**
   - Small datasets where simplicity and recursion are desired.
   - Situations where a conceptual understanding of recursion is more beneficial than performance optimization.

2. **When Not to Use:**
   - Large datasets due to the high time complexity.
   - Situations where performance is critical.

3. **Examples of Use:**
   - Teaching recursion and basic sorting concepts.
   - Sorting a small, manageable list where recursive logic is preferred for clarity.

4. **Comparison with Other Algorithms:**
   - **Recursive Bubble Sort vs Iterative Bubble Sort:** Both have similar time complexities, but the recursive version uses additional stack space.
   - **Recursive Bubble Sort vs Quick Sort:** Quick sort is much faster for larger datasets, with an average time complexity of \(O(N \log N)\).
   - **Recursive Bubble Sort vs Merge Sort:** Merge sort is also more efficient for large datasets, with a guaranteed time complexity of \(O(N \log N)\), but requires additional space for merging.

This summary encapsulates the essence of the Recursive Bubble Sort algorithm, highlighting its approach, implementation, and practical use cases.
