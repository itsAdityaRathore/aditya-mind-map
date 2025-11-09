### **1. Sliding Window Template**

Used for problems involving contiguous subarrays or substrings.

### **Java Code**

```java
java
Copy code
public int slidingWindow(int[] arr, int k) {
    int n = arr.length;
    int left = 0, currentSum = 0, maxSum = Integer.MIN_VALUE;

    for (int right = 0; right < n; right++) {
        currentSum += arr[right];  // Expand the window
        if (right - left + 1 == k) {  // Check window size
            maxSum = Math.max(maxSum, currentSum);
            currentSum -= arr[left];  // Shrink the window
            left++;
        }
    }

    return maxSum;
}

```

---

### **2. Two-Pointer Technique**

Ideal for problems involving sorted arrays, subsequences, or palindromes.

### **Java Code**

```java
java
Copy code
public int[] twoSumSorted(int[] arr, int target) {
    int left = 0, right = arr.length - 1;

    while (left < right) {
        int currentSum = arr[left] + arr[right];
        if (currentSum == target) {
            return new int[]{left, right};
        } else if (currentSum < target) {
            left++;
        } else {
            right--;
        }
    }

    return new int[]{-1, -1};
}

```

---

### **3. Binary Search Template**

Efficient for finding elements in sorted arrays or solving optimization problems.

### **Java Code**

```java
java
Copy code
public int binarySearch(int[] arr, int target) {
    int left = 0, right = arr.length - 1;

    while (left <= right) {
        int mid = left + (right - left) / 2;

        if (arr[mid] == target) {
            return mid;
        } else if (arr[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }

    return -1;
}

```

---

### **4. Backtracking Template**

Used for problems that involve generating all possible solutions or searching with constraints.

### **Java Code**

```java
java
Copy code
public void backtrack(List<Integer> path, int[] options, List<List<Integer>> result) {
    if (isSolution(path)) {
        result.add(new ArrayList<>(path));
        return;
    }

    for (int option : options) {
        if (isValid(option, path)) {
            path.add(option);  // Choose
            backtrack(path, options, result);  // Explore
            path.remove(path.size() - 1);  // Un-choose
        }
    }
}

// Helper methods (example purposes)
private boolean isSolution(List<Integer> path) {
    // Add your base condition here
    return false;
}

private boolean isValid(int option, List<Integer> path) {
    // Add validation logic here
    return true;
}

```

---

### **5. Dynamic Programming Template**

### **Top-Down (Recursion + Memoization)**

```java
java
Copy code
public int dpTopDown(int n, Map<Integer, Integer> memo) {
    if (memo.containsKey(n)) return memo.get(n);
    if (n == 0 || n == 1) return n;

    int result = dpTopDown(n - 1, memo) + dpTopDown(n - 2, memo);
    memo.put(n, result);
    return result;
}

```

### **Bottom-Up (Tabulation)**

```java
java
Copy code
public int dpBottomUp(int n) {
    if (n == 0 || n == 1) return n;

    int[] dp = new int[n + 1];
    dp[0] = 0;
    dp[1] = 1;

    for (int i = 2; i <= n; i++) {
        dp[i] = dp[i - 1] + dp[i - 2];
    }

    return dp[n];
}

```

---

### **6. Graph Traversal Templates**

### **Breadth-First Search (BFS)**

```java
java
Copy code
public void bfs(Map<Integer, List<Integer>> graph, int start) {
    Queue<Integer> queue = new LinkedList<>();
    Set<Integer> visited = new HashSet<>();

    queue.add(start);
    visited.add(start);

    while (!queue.isEmpty()) {
        int node = queue.poll();
        processNode(node);

        for (int neighbor : graph.get(node)) {
            if (!visited.contains(neighbor)) {
                visited.add(neighbor);
                queue.add(neighbor);
            }
        }
    }
}

// Helper method to process a node
private void processNode(int node) {
    System.out.println(node);
}

```

### **Depth-First Search (DFS)**

```java
java
Copy code
public void dfs(Map<Integer, List<Integer>> graph, int node, Set<Integer> visited) {
    if (visited.contains(node)) return;

    visited.add(node);
    processNode(node);

    for (int neighbor : graph.get(node)) {
        dfs(graph, neighbor, visited);
    }
}

```

---

### **7. Greedy Algorithm Template**

### **Java Code**

```java
java
Copy code
public int greedyAlgorithm(int[][] intervals) {
    Arrays.sort(intervals, Comparator.comparingInt(a -> a[1]));  // Sort by ending time
    int count = 0, lastEnd = Integer.MIN_VALUE;

    for (int[] interval : intervals) {
        if (interval[0] >= lastEnd) {
            count++;
            lastEnd = interval[1];
        }
    }

    return count;
}

```