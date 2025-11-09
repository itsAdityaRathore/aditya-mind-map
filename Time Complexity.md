## **1. What is Time Complexity?**

Time complexity measures the number of operations an algorithm performs relative to the size of its input. It is expressed using **Big-O notation**.

---

## **2. Common Time Complexities**

|Big-O Notation|Description|Example Algorithm|
|---|---|---|
|**O(1)**|Constant Time|Accessing an array element|
|**O(log N)**|Logarithmic Time|Binary search|
|**O(N)**|Linear Time|Traversing an array|
|**O(N log N)**|Linearithmic Time|Merge sort, Quick sort|
|**O(N²)**|Quadratic Time|Nested loops (e.g., Bubble Sort)|
|**O(2ⁿ)**|Exponential Time|Solving subsets recursively|
|**O(N!)**|Factorial Time|Permutations generation|

---

## **3. Examples with Code and Time Complexity**

### **a) Constant Time: O(1)**

### Example:

Accessing an element in an array or performing a simple arithmetic operation.

### Code:

```java
java
Copy code
public int getElement(int[] arr, int index) {
    return arr[index];  // Accessing an element takes O(1) time
}

```

---

### **b) Logarithmic Time: O(logN)**

### Example:

Binary search reduces the search space by half each iteration.

### Code:

```java
java
Copy code
public int binarySearch(int[] arr, int target) {
    int left = 0, right = arr.length - 1;

    while (left <= right) {
        int mid = left + (right - left) / 2;

        if (arr[mid] == target) return mid;
        else if (arr[mid] < target) left = mid + 1;
        else right = mid - 1;
    }

    return -1;
}

```

### Time Complexity:

- Dividing the array in half at each step leads to O(logN).

---

### **c) Linear Time: O(N)**

### Example:

Traversing an array or performing a single loop.

### Code:

```java
java
Copy code
public int findMax(int[] arr) {
    int max = arr[0];
    for (int num : arr) {
        if (num > max) max = num;
    }
    return max;
}

```

### Time Complexity:

- The loop iterates N times, so the complexity is O(N).

---

### **d) Linearithmic Time: O(N log N)**

### Example:

Sorting algorithms like Merge Sort or Quick Sort.

### Code:

```java
java
Copy code
public void mergeSort(int[] arr, int left, int right) {
    if (left < right) {
        int mid = left + (right - left) / 2;
        mergeSort(arr, left, mid);
        mergeSort(arr, mid + 1, right);
        merge(arr, left, mid, right);  // Merging sorted halves
    }
}

```

### Time Complexity:

- Splitting the array takes O(log N).
- Merging takes O(N).
- Combined: O(N log N).

---

### **e) Quadratic Time: O(N²)**

### Example:

Nested loops for comparing pairs, such as in Bubble Sort.

### Code:

```java
java
Copy code
public void bubbleSort(int[] arr) {
    int n = arr.length;
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                // Swap elements
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
}

```

### Time Complexity:

- Two nested loops each iterating N times lead to **O(N²)**.

---

### **f) Exponential Time: O(2ⁿ)**

### Example:

Generating all subsets of a set or solving the Tower of Hanoi problem.

### Code:

```java
java
Copy code
public void generateSubsets(String str, int index, String current) {
    if (index == str.length()) {
        System.out.println(current);
        return;
    }
    generateSubsets(str, index + 1, current + str.charAt(index));  // Include current character
    generateSubsets(str, index + 1, current);  // Exclude current character
}

```

### Time Complexity:

- Each character can either be included or excluded, leading to 2ⁿ combinations.

---

### **g) Factorial Time: O(N!)**

### Example:

Generating all permutations of a string.

### Code:

```java
java
Copy code
public void generatePermutations(String str, int left, int right) {
    if (left == right) {
        System.out.println(str);
        return;
    }
    for (int i = left; i <= right; i++) {
        str = swap(str, left, i);
        generatePermutations(str, left + 1, right);
        str = swap(str, left, i);  // Backtrack
    }
}

private String swap(String str, int i, int j) {
    char[] chars = str.toCharArray();
    char temp = chars[i];
    chars[i] = chars[j];
    chars[j] = temp;
    return String.valueOf(chars);
}

```

### Time Complexity:

- For N characters, N! permutations are generated.

---

## **4. Strategies to Optimize Time Complexity**

- **Avoid Nested Loops**:
    - Replace O(N²) algorithms with efficient alternatives like O(NlogN).
- **Use Hashing**:
    - HashMaps or HashSets can reduce lookups from O(N) to O(1).
- **Apply Divide and Conquer**:
    - Algorithms like Merge Sort and Binary Search use this technique to optimize performance.
- **Dynamic Programming**:
    - Avoid redundant computations using memoization or tabulation.
- **Greedy Algorithms**:
    - When applicable, they provide faster O(N) solutions.
- **Precompute Results**:
    - For repetitive calculations, store results in an array for O(1) access.