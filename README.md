# Programming-Assignment-2-Algorithmic-Warm-up-Fibonacci-number-
This repository demonstrates two methods to calculate Fibonacci numbers:  A naive recursive approach. An optimized iterative approach using dynamic programming. The project ensures accuracy through rigorous testing and improves efficiency for large inputs. also i used c++ for coding. 

---

# Fibonacci Sequence Optimization

## 🌀 Introduction to Fibonacci Numbers

The Fibonacci sequence is a series of numbers where each number is the sum of the two preceding ones. It starts like this:

```
0, 1, 1, 2, 3, 5, 8, 13, ...
```

### Formula:
\[
F(n) =
\begin{cases} 
0 & \text{if } n = 0 \\
1 & \text{if } n = 1 \\
F(n-1) + F(n-2) & \text{if } n > 1
\end{cases}
\]

### Applications:
- Fibonacci numbers are widely used in computer algorithms, nature (e.g., the arrangement of leaves), art, and financial modeling.

---

## 🛠 Fixes and Optimizations

### 1. **Naive Algorithm (Original Code)**

The original implementation used a **recursive approach**:

```cpp
int fibonacci_naive(int n) {
    if (n <= 1)
        return n;
    return fibonacci_naive(n - 1) + fibonacci_naive(n - 2);
}
```

- **How It Works**:
  - The function calls itself recursively for \(n-1\) and \(n-2\) until it reaches the base cases (\(n = 0\) or \(n = 1\)).
- **Drawbacks**:
  - **Inefficient**: It recalculates the same values multiple times, resulting in an exponential time complexity (\(O(2^n)\)).
  - **Slow for Large Inputs**: For \(n = 40\), it takes a significant amount of time.

---

### 2. **Optimized Algorithm (Fixed Code)**

I implemented an **iterative dynamic programming approach** to address the inefficiencies:

```cpp
int fibonacci_fast(int n) {
    if (n <= 1)
        return n;

    std::vector<int> fib(n + 1);
    fib[0] = 0;
    fib[1] = 1;

    for (int i = 2; i <= n; ++i) {
        fib[i] = fib[i - 1] + fib[i - 2];
    }

    return fib[n];
}
```

- **How It Works**:
  - Instead of recalculating values, it computes Fibonacci numbers sequentially and stores them in an array.
  - The array `fib` keeps the Fibonacci values from `fib[0]` to `fib[n]`.
  - Each Fibonacci number is calculated using the two preceding numbers (\(fib[i] = fib[i-1] + fib[i-2]\)).

- **Benefits**:
  - **Time Complexity**: \(O(n)\) (linear growth)
  - **Space Complexity**: \(O(n)\) (to store the array)

---

### 3. **Testing and Validation**

We used the `test_solution()` function to validate the optimized algorithm against the naive approach for small inputs:

```cpp
void test_solution() {
    assert(fibonacci_fast(3) == 2);
    assert(fibonacci_fast(10) == 55);
    for (int n = 0; n < 20; ++n)
        assert(fibonacci_fast(n) == fibonacci_naive(n));
    std::cout << "All tests passed!" << '\n';
}
```

- **How It Works**:
  - Runs multiple test cases to check if the optimized algorithm matches the results of the naive implementation.
  - Uses `assert` statements to confirm correctness.
  - If a test fails, the program stops with an error message.

---


## 🔄 Comparison: Naive vs Optimized

| **Aspect**          | **Naive Approach**                  | **Optimized Approach**              |
|----------------------|--------------------------------------|--------------------------------------|
| **Time Complexity**  | \(O(2^n)\)                          | \(O(n)\)                            |
| **Space Complexity** | \(O(1)\)                            | \(O(n)\)                            |
| **Performance**      | Very slow for large \(n\)           | Handles large \(n\) efficiently     |
| **Practical Use**    | Demonstrative purpose only          | Real-world application-ready        |

