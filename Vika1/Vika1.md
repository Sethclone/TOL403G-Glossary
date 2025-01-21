# Review of Time Complexity in Algorithms

## Time Complexities

Time complexities describe the running time of algorithms relative to the size of the input (`n`):  
`O(1)`, `O(log n)`, `O(n)`, `O(n log n)`, etc.

### Example: Insertion Sort  
Insertion sort arranges an array in ascending order. Example code for insertion sort can be found online.  
To determine the running time of insertion sort:

1. Each line in the algorithm takes constant time, denoted as `cᵢ` for line `i`.  
   These constants depend on factors such as:
   - The operation performed (comparison, assignment, etc.)
   - The programming language used
   - The hardware running the program

2. **Counting operations**:  
   - **For loop**:
     - Comparisons are performed `n` times:
       - `(n-1)` times for values `2` to `n`
       - Once more when `j > n`
   - **Basic operations** (Lines 3, 4, 8):
     - Performed `(n-1)` times each
   - **While loop**:
     - The number of iterations varies depending on the ordering of values in the array.

3. **Best Case**:
   - When the array is already sorted (`A[i-1] < A[i]` for all `n`).
   - Time complexity: `O(n)`

4. **Worst Case**:
   - When the array is sorted in descending order (`A[i-1] > A[i]` for all `n`).
   - Time complexity: `O(n²)`

5. **Suitability of `O(n²)`**:
   - Useful for:
     - Small datasets (`n < 50`)
     - Nearly sorted datasets
     - Sorting portions of a larger dataset

---

## Asymptotic Notation  

### Big-O Notation (`O`)
`O(g)` represents the set of all functions that grow as fast or slower than `g`.  
For example, is `f(x) = x²` in `O(x²)`?  

To prove:  
- Assume `k = 1` and `x > 1`. Then:  
  - `x² > 1` and `x² > x`  
  - `0 <= f(x) = x² + 2x + 1 <= x² + 2x² + x² = 4x²`  

Thus, for `x > k = 1`, we have `f(x) <= 4x²`.  
We can use `k = 1` and `C = 4` as witnesses, proving `f(x) = O(x²)`.

### Steps to Find Big-O Notation:
1. Identify the dominant term.
2. Find the order of growth.
3. Write the `O` notation.
4. Simplify the notation.

Example: For `f(n) = 3n³ + 2n² + 5n + 1`:
- Dominant term: `3n³`
- Order of growth: `n³`
- `O` notation: `O(n³)`
- Simplified: `O(n³)`

---

## Definitions: Big-O, Omega, and Theta

- **Big-O (`O`)**: `f(n) <= c*g(n)` for all `n >= n₀`  
- **Omega (`Ω`)**: `f(n) >= c*g(n)` for all `n >= n₀`  
- **Theta (`Θ`)**: `C₁*g(n) <= f(n) <= C₂*g(n)` for `n >= n₀`

### Parameters:
- `f(n)` is the function being analyzed.
- `g(n)` is a bounding function.
- `C`, `C₁`, `C₂` are constants.
- `n₀` is the minimum size of `n`.

This defines:
- **Worst Case**: `O`
- **Best Case**: `Ω`
- **Average Case**: `Θ`

---

## Additional Asymptotic Notations

### Little-o (`o`):
- Represents functions that grow strictly slower than `g`.  
- Notation: `f = o(g)` or `f(n) = o(g(n))`.  
Example:  
- `f(n) = n²`, `g(n) = n³`  
- Since `f` grows slower than `g`, `f = o(g)`.

### Little-Omega (`ω`):
- Represents functions that grow strictly faster than `g`.  
- Notation: `f(n) = ω(g(n))`.  
Example:  
- `n²/2 = ω(log(n))`, but `n²/2 ≠ ω(n²)`.

---

## Transitivity of Asymptotic Notations

For any functions `f(n)`, `g(n)`, and `h(n)`:
- If `f(n) = Θ(g(n))` and `g(n) = Θ(h(n))` ⇒ `f(n) = Θ(h(n))`
- If `f(n) = O(g(n))` and `g(n) = O(h(n))` ⇒ `f(n) = O(h(n))`
- If `f(n) = Ω(g(n))` and `g(n) = Ω(h(n))` ⇒ `f(n) = Ω(h(n))`
- If `f(n) = o(g(n))` and `g(n) = o(h(n))` ⇒ `f(n) = o(h(n))`
- If `f(n) = ω(g(n))` and `g(n) = ω(h(n))` ⇒ `f(n) = ω(h(n))`

---

## Self-Referential Properties  

For all functions `f(n)`:
- `f(n) = Θ(f(n))`
- `f(n) = O(f(n))`
- `f(n) = Ω(f(n))`

--- 

## Simplified Growth Order of Functions  
`1 < log(n) < √n < n < n log(n) < n² < n³ < 2ⁿ < n!`

---

## Constant Time Operations (`O(1)`):
- Arithmetic: `+`, `-`, `*`, `/`, `//`
- Logical: `and`, `or`, `not`
- Comparisons: `x < y`, `x == y`
- Bitwise operations
- Memory read/write
