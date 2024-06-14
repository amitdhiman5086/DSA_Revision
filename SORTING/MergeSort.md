### Merge Sort Algorithm

---

#### Problem Statement:

Given an array of size \( n \), sort the array using the Merge Sort algorithm.

#### Examples:

1. **Input:** \( N = 5, \text{arr}[] = \{4, 2, 1, 6, 7\} \)
   **Output:** \( 1, 2, 4, 6, 7 \)

2. **Input:** \( N = 7, \text{arr}[] = \{3, 2, 8, 5, 1, 4, 23\} \)
   **Output:** \( 1, 2, 3, 4, 5, 8, 23 \)

---

#### Intuition:

Merge Sort is a classic divide-and-conquer algorithm. It works by recursively dividing the array into two halves, sorting each half, and then merging the sorted halves back together.

**Steps:**

1. **Divide** the array into two halves.
2. **Conquer** by sorting each half recursively.
3. **Merge** the two sorted halves.

The merging process assumes both halves are already sorted and combines them into a single sorted array.

---

#### Approach:

1. **Function Definitions:**
   - **`mergeSort(arr, low, high)`**: Divides the array into two halves and calls itself recursively on each half until the base case is reached.
   - **`merge(arr, low, mid, high)`**: Merges two sorted halves into a single sorted array.

2. **Recursive Division:**
   - The `mergeSort` function calculates the middle index and recursively sorts the left and right halves.
   - Base Case: When the sub-array has only one element (or none), it is considered sorted.

3. **Merging Process:**
   - Use two pointers to traverse the two halves.
   - Compare elements from both halves and build a temporary sorted array.
   - Copy the sorted elements back to the original array.

---

#### Pseudocode:

1. **Merge Sort Function:**

```cpp
void mergeSort(vector<int> &arr, int low, int high) {
    if (low >= high) return; // Base case: single element is already sorted

    int mid = (low + high) / 2; // Find the middle point
    mergeSort(arr, low, mid); // Sort the first half
    mergeSort(arr, mid + 1, high); // Sort the second half
    merge(arr, low, mid, high); // Merge the sorted halves
}
```

2. **Merge Function:**

```cpp
void merge(vector<int> &arr, int low, int mid, int high) {
    vector<int> temp; // Temporary array to store merged elements
    int left = low; // Starting index for the left half
    int right = mid + 1; // Starting index for the right half

    // Merge elements into temp in sorted order
    while (left <= mid && right <= high) {
        if (arr[left] <= arr[right]) {
            temp.push_back(arr[left]);
            left++;
        } else {
            temp.push_back(arr[right]);
            right++;
        }
    }

    // Copy any remaining elements from the left half
    while (left <= mid) {
        temp.push_back(arr[left]);
        left++;
    }

    // Copy any remaining elements from the right half
    while (right <= high) {
        temp.push_back(arr[right]);
        right++;
    }

    // Transfer sorted elements back to the original array
    for (int i = low; i <= high; i++) {
        arr[i] = temp[i - low];
    }
}
```

---

#### Full Code Implementation:

**C++ Implementation:**

```cpp
#include <bits/stdc++.h>
using namespace std;

void merge(vector<int> &arr, int low, int mid, int high) {
    vector<int> temp; // Temporary array
    int left = low; // Starting index for left subarray
    int right = mid + 1; // Starting index for right subarray

    // Merge the two halves in sorted order
    while (left <= mid && right <= high) {
        if (arr[left] <= arr[right]) {
            temp.push_back(arr[left]);
            left++;
        } else {
            temp.push_back(arr[right]);
            right++;
        }
    }

    // Copy remaining elements from the left half
    while (left <= mid) {
        temp.push_back(arr[left]);
        left++;
    }

    // Copy remaining elements from the right half
    while (right <= high) {
        temp.push_back(arr[right]);
        right++;
    }

    // Copy sorted elements back to the original array
    for (int i = low; i <= high; i++) {
        arr[i] = temp[i - low];
    }
}

void mergeSort(vector<int> &arr, int low, int high) {
    if (low >= high) return; // Base case: one or no elements

    int mid = (low + high) / 2; // Find the middle point
    mergeSort(arr, low, mid); // Sort the left half
    mergeSort(arr, mid + 1, high); // Sort the right half
    merge(arr, low, mid, high); // Merge the sorted halves
}

int main() {
    vector<int> arr = {9, 4, 7, 6, 3, 1, 5};
    int n = arr.size();

    cout << "Before Sorting: ";
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    mergeSort(arr, 0, n - 1);

    cout << "After Sorting: ";
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    return 0;
}
```

**Output:**

```
Before Sorting: 9 4 7 6 3 1 5 
After Sorting: 1 3 4 5 6 7 9 
```

---

#### Complexity Analysis:

1. **Time Complexity:**
   - **Worst-case:** \( O(n \log n) \)
   - **Average-case:** \( O(n \log n) \)
   - **Best-case:** \( O(n \log n) \)
   - Each division takes \( \log n \) steps, and merging takes \( O(n) \) time. Thus, the overall complexity is \( O(n \log n) \).

2. **Space Complexity:**
   - **Space complexity:** \( O(n) \)
   - **Auxiliary Space Complexity:** \( O(n) \)
   - We use an additional array for merging, requiring \( O(n) \) extra space.

---

#### Summary:

1. **When to Use:**
   - Efficient for large datasets.
   - Stable sorting algorithm (maintains the order of equal elements).
   - Preferred when the entire data set must be sorted and the extra space is available.

2. **When Not to Use:**
   - In-place sorting is needed (e.g., in embedded systems with limited memory).
   - Simpler algorithms (e.g., insertion sort) may be preferred for very small datasets due to lower overhead.

3. **Comparison with Other Algorithms:**
   - **Merge Sort vs Quick Sort:** Quick Sort is generally faster but has a worst-case time complexity of \( O(n^2) \). Merge Sort is more predictable with consistent \( O(n \log n) \) performance.
   - **Merge Sort vs Bubble Sort/Insertion Sort:** Bubble Sort and Insertion Sort are \( O(n^2) \) algorithms, making them inefficient for large datasets compared to Merge Sort.
   - **Merge Sort vs Heap Sort:** Heap Sort also offers \( O(n \log n) \) performance but is in-place and not stable.

Merge Sort is a powerful sorting algorithm that balances performance and reliability, making it a fundamental algorithm in computer science and an excellent tool for large-scale data sorting tasks.