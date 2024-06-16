## Approach 1: Using a Temporary Array

### Rotating to the Right

**Steps:**

1. Copy the last \( k \) elements to a temporary array.
2. Shift the first \( n-k \) elements to the right by \( k \) positions.
3. Copy the elements from the temporary array to the first \( k \) positions in the main array.

**Code:**

```cpp
#include <iostream>
using namespace std;

void rotateRight(int arr[], int n, int k) {
    if (n == 0) return;
    k = k % n;  // In case k is larger than n
    if (k == 0) return;

    int temp[k];
    for (int i = 0; i < k; i++) {
        temp[i] = arr[n - k + i];
    }
    for (int i = n - 1; i >= k; i--) {
        arr[i] = arr[i - k];
    }
    for (int i = 0; i < k; i++) {
        arr[i] = temp[i];
    }
}

int main() {
    int n = 7;
    int arr[] = {1, 2, 3, 4, 5, 6, 7};
    int k = 2;
    rotateRight(arr, n, k);
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    return 0;
}
```

**Output:**

```plaintext
6 7 1 2 3 4 5
```

### Rotating to the Left

**Steps:**

1. Copy the first \( k \) elements to a temporary array.
2. Shift the remaining elements to the left by \( k \) positions.
3. Copy the elements from the temporary array to the last \( k \) positions in the main array.

**Code:**

```cpp
#include <iostream>
using namespace std;

void rotateLeft(int arr[], int n, int k) {
    if (n == 0) return;
    k = k % n;  // In case k is larger than n
    if (k == 0) return;

    int temp[k];
    for (int i = 0; i < k; i++) {
        temp[i] = arr[i];
    }
    for (int i = 0; i < n - k; i++) {
        arr[i] = arr[i + k];
    }
    for (int i = 0; i < k; i++) {
        arr[n - k + i] = temp[i];
    }
}

int main() {
    int n = 7;
    int arr[] = {1, 2, 3, 4, 5, 6, 7};
    int k = 2;
    rotateLeft(arr, n, k);
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    return 0;
}
```

**Output:**

```plaintext
3 4 5 6 7 1 2
```

## Approach 2: Using the Reversal Algorithm

### Rotating to the Right

**Steps:**

1. Reverse the last \( k \) elements.
2. Reverse the first \( n-k \) elements.
3. Reverse the whole array.

**Code:**

```cpp
#include <iostream>
using namespace std;

void reverse(int arr[], int start, int end) {
    while (start < end) {
        int temp = arr[start];
        arr[start] = arr[end];
        arr[end] = temp;
        start++;
        end--;
    }
}

void rotateRight(int arr[], int n, int k) {
    k = k % n;  // In case k is larger than n
    reverse(arr, n - k, n - 1);  // Step 1
    reverse(arr, 0, n - k - 1);  // Step 2
    reverse(arr, 0, n - 1);      // Step 3
}

int main() {
    int n = 7;
    int arr[] = {1, 2, 3, 4, 5, 6, 7};
    int k = 2;
    rotateRight(arr, n, k);
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    return 0;
}
```

**Output:**

```plaintext
6 7 1 2 3 4 5
```

### Rotating to the Left

**Steps:**

1. Reverse the first \( k \) elements.
2. Reverse the remaining \( n-k \) elements.
3. Reverse the whole array.

**Code:**

```cpp
#include <iostream>
using namespace std;

void reverse(int arr[], int start, int end) {
    while (start < end) {
        int temp = arr[start];
        arr[start] = arr[end];
        arr[end] = temp;
        start++;
        end--;
    }
}

void rotateLeft(int arr[], int n, int k) {
    k = k % n;  // In case k is larger than n
    reverse(arr, 0, k - 1);      // Step 1
    reverse(arr, k, n - 1);      // Step 2
    reverse(arr, 0, n - 1);      // Step 3
}

int main() {
    int n = 7;
    int arr[] = {1, 2, 3, 4, 5, 6, 7};
    int k = 2;
    rotateLeft(arr, n, k);
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    return 0;
}
```

**Output:**

```plaintext
3 4 5 6 7 1 2
```

## Conclusion

Both approaches have their own advantages. The temporary array method is straightforward but requires extra space proportional to \( k \). The reversal algorithm is more space-efficient, requiring only \( O(1) \) extra space, but involves multiple reversals. Choose the method that best suits your constraints and preferences.
