### Quick Sort Algorithm

#### Problem Statement
- **Task**: Given an array of \( n \) integers, sort the array using the Quicksort method.
- **Examples**:
  - Input: \( N = 5 \), Arr[] = {4, 1, 7, 9, 3}
    - Output: 1 3 4 7 9
  - Input: \( N = 8 \), Arr[] = {4, 6, 2, 5, 7, 9, 1, 3}
    - Output: 1 2 3 4 5 6 7 9

#### Intuition
- **Divide-and-Conquer**: Quick Sort is a divide-and-conquer algorithm.
- **No Extra Array Needed**: Unlike Merge Sort, Quick Sort doesn't use an extra array for sorting, making it more space-efficient.
- **Steps**:
  1. Pick a pivot and place it in its correct position.
  2. Shift smaller elements to the left and larger elements to the right of the pivot.
  3. Apply the steps recursively to the left and right subarrays.

#### Detailed Steps with Example
1. **Choose a Pivot**: Any element in the array can be chosen as the pivot (e.g., first, last, median, random).
   - Example Array: {4, 6, 2, 5, 7, 9, 1, 3}
   - Pivot Chosen: 4 (first element in this example)

2. **Partitioning**:
   - Place the pivot in its correct position.
   - Shift elements: smaller elements to the left, larger elements to the right.
   - After partitioning: {3, 2, 1, 4, 6, 5, 7, 9}

3. **Recursion**:
   - Apply the steps recursively to the left and right subarrays until the size of the unsorted part becomes 1.

#### Implementation Approach
- Use two indices (low and high) to define the range of the subarray.
- **quickSort() Function**:
  - Use the `partition()` function to place the pivot in its correct position and get the partition index.
  - Recursively apply `quickSort()` to the left and right subarrays.

#### Pseudocode
**quickSort() Function**:
1. If low < high:
   - partitionIndex = partition(arr, low, high)
   - quickSort(arr, low, partitionIndex - 1)
   - quickSort(arr, partitionIndex + 1, high)

**partition() Function**:
1. Select pivot (e.g., arr[low])
2. Use two pointers (i and j):
   - i moves forward to find elements greater than the pivot.
   - j moves backward to find elements smaller than the pivot.
3. Swap elements arr[i] and arr[j] if i < j.
4. Continue until j < i.
5. Swap pivot with arr[j] and return j.

#### Example Code in C++
```cpp
#include <bits/stdc++.h>
using namespace std;

int partition(vector<int> &arr, int low, int high) {
    int pivot = arr[low];
    int i = low;
    int j = high;

    while (i < j) {
        while (arr[i] <= pivot && i <= high - 1) {
            i++;
        }

        while (arr[j] > pivot && j >= low + 1) {
            j--;
        }
        if (i < j) swap(arr[i], arr[j]);
    }
    swap(arr[low], arr[j]);
    return j;
}

void qs(vector<int> &arr, int low, int high) {
    if (low < high) {
        int pIndex = partition(arr, low, high);
        qs(arr, low, pIndex - 1);
        qs(arr, pIndex + 1, high);
    }
}

vector<int> quickSort(vector<int> arr) {
    qs(arr, 0, arr.size() - 1);
    return arr;
}

int main() {
    vector<int> arr = {4, 6, 2, 5, 7, 9, 1, 3};
    int n = arr.size();
    cout << "Before Using quick Sort: " << endl;
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;

    arr = quickSort(arr);
    cout << "After Using quick sort: " << "\n";
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << "\n";
    return 0;
}
```

#### Time and Space Complexity
- **Best and Average Case Time Complexity**: \( O(N \log N) \)
  - Dividing the array in each step takes \( \log N \) steps, and partitioning takes \( N \) steps.
- **Worst Case Time Complexity**: \( O(N^2) \)
  - Occurs when the pivot is the greatest or smallest element.
- **Space Complexity**: \( O(1) \) for in-place sorting + \( O(N) \) auxiliary stack space for recursion.