Of course! Here is a well-commented and reusable C++ template for 2D Prefix Sums, designed for a competitive programming context with multiple test cases.

The core idea is to precompute the sum of all rectangles starting from the top-left corner `(1, 1)`. This allows us to find the sum of any arbitrary sub-rectangle in `O(1)` time after an initial `O(n*m)` preprocessing step.

### Key Concepts

1.  **1-Based Indexing:** The template uses 1-based indexing for the matrix. This simplifies the formulas for both building the prefix sum array and querying it, as you don't need to handle edge cases for row 0 or column 0. The arrays are therefore sized `(n+1) x (m+1)`.

2.  **Building the Prefix Sum Array:**
    The sum of the rectangle from `(1, 1)` to `(i, j)` is calculated using the principle of inclusion-exclusion:
    `prefix_sum[i][j] = value[i][j] + prefix_sum[i-1][j] + prefix_sum[i][j-1] - prefix_sum[i-1][j-1]`

    *   `value[i][j]`: The value of the current cell.
    *   `prefix_sum[i-1][j]`: Sum of the rectangle just above the current cell.
    *   `prefix_sum[i][j-1]`: Sum of the rectangle just to the left of the current cell.
    *   `prefix_sum[i-1][j-1]`: This area was included in both of the previous sums, so we subtract it once to correct the double-counting.

3.  **Querying the Sum of a Sub-rectangle:**
    To find the sum of a rectangle with top-left corner `(r1, c1)` and bottom-right corner `(r2, c2)`, we again use inclusion-exclusion:
    `Sum = prefix_sum[r2][c2] - prefix_sum[r1-1][c2] - prefix_sum[r2][c1-1] + prefix_sum[r1-1][c1-1]`

    *   `prefix_sum[r2][c2]`: The sum of the large rectangle from `(1,1)` to `(r2,c2)`.
    *   `prefix_sum[r1-1][c2]`: Subtract the unwanted area above our target rectangle.
    *   `prefix_sum[r2][c1-1]`: Subtract the unwanted area to the left of our target rectangle.
    *   `prefix_sum[r1-1][c1-1]`: The top-left corner area was subtracted twice, so we add it back once.

---

### C++ Template for 2D Prefix Sum

```cpp
#include <iostream>
#include <vector>


using namespace std;

using ll = long long;

// The main logic for a single test case is encapsulated in this function.
void solve() {
    // ---- 1. INPUT ----
    int n, m; // n: number of rows, m: number of columns
    cin >> n >> m; // Read the dimensions of the matrix.

    
    vector<vector<ll>> prefix_sum(n + 1, vector<ll>(m + 1, 0));

       for (int i = 1; i <= n; ++i) {
        for (int j = 1; j <= m; ++j) {
            ll current_value; // Variable to hold the value of the current cell in the original matrix.
            cin >> current_value; // Read the value for cell (i, j).

            // This is the core formula for building the 2D prefix sum array.
            // It calculates the sum of the rectangle from (1,1) to (i,j).
            prefix_sum[i][j] = current_value             // The value of the current cell.
                               + prefix_sum[i - 1][j]    // Sum of the rectangle above.
                               + prefix_sum[i][j - 1]    // Sum of the rectangle to the left.
                               - prefix_sum[i - 1][j - 1]; // Subtract the top-left rectangle that was double-counted.
        }
    }

    // ---- 4. QUERY FUNCTION ----
    // This lambda function calculates the sum of a sub-rectangle in O(1).
    // It captures the 'prefix_sum' array by reference [&] to avoid copying it.
    auto query_sum = [&](int r1, int c1, int r2, int c2) {
        // This is the core formula for querying the sum of a sub-rectangle.
        // It uses the precomputed values to find the sum in constant time.
        return prefix_sum[r2][c2]                 // Sum of the large rectangle from (1,1) to (r2,c2).
               - prefix_sum[r1 - 1][c2]           // Subtract the rectangle above the query area.
               - prefix_sum[r2][c1 - 1]           // Subtract the rectangle to the left of the query area.
               + prefix_sum[r1 - 1][c1 - 1];      // Add back the top-left corner that was double-subtracted.
    };

    // ---- 5. EXAMPLE USAGE ----
    // This section demonstrates how to use the query_sum function.
    // In a real problem, you would read the number of queries 'q' and their coordinates here.
    cout << "--- Example Queries ---" << endl;

    // Example 1: Sum of the entire matrix from (1,1) to (n,m)
    cout << "Sum of rectangle from (1,1) to (" << n << "," << m << "): "
         << query_sum(1, 1, n, m) << endl;

    // Example 2: Sum of a single cell, e.g., (2,2)
    if (n >= 2 && m >= 2) {
        cout << "Sum of rectangle from (2,2) to (2,2): "
             << query_sum(2, 2, 2, 2) << endl;
    }
    
    // Example 3: A sub-rectangle query, e.g., from (2,2) to (3,4)
    if (n >= 3 && m >= 4) {
        cout << "Sum of rectangle from (2,2) to (3,4): "
             << query_sum(2, 2, 3, 4) << endl;
    }
    
    // In a contest, you would have a loop like this:
    /*
    int q;
    cin >> q;
    while(q--) {
        int r1, c1, r2, c2;
        cin >> r1 >> c1 >> r2 >> c2;
        cout << query_sum(r1, c1, r2, c2) << "\n";
    }
    */
}

// The main function, the entry point of the program.
int main() {
    // ---- BOILERPLATE FOR FASTER I/O ----
    // Unties cin from cout.
    ios_base::sync_with_stdio(false);
    // Disables the flushing of cout before every cin.
    cin.tie(NULL);

    //int t; // Variable to store the number of test cases.
    //cin >> t; // Read the number of test cases.
    
    // Loop that runs 't' times, processing one test case in each iteration.
    //while (t--) {
      //  solve(); // Call the function that contains the logic for a single test case.
   // }

    return 0; // Indicates that the program executed successfully.
}
```

### How to Use the Template

1.  **Copy-Paste:** Copy the entire code into your editor.
2.  **Input Format:** The code expects the input for each test case to be in the following format:
    *   First line: `n m` (number of rows and columns).
    *   Next `n` lines: `m` space-separated integers, representing the matrix.
    *   (Optional) After the matrix, you can add your query logic, for example, by reading `q` (number of queries) and then `q` lines of `r1 c1 r2 c2`.
3.  **Adapt the Query Section:** The "EXAMPLE USAGE" part inside the `solve()` function is a placeholder. Modify it to fit the specific problem's query requirements. Uncomment and adapt the loop for `q` queries as needed.
4.  **Coordinates:** Remember that all queries `(r1, c1, r2, c2)` should use **1-based indexing** to match the implementation. `r1` should be less than or equal to `r2`, and `c1` should be less than or equal to `c2`.

#PrefixSuffixProduct #Matrix #precompute
```c++
#include <iostream>
#include <vector>
#include <string>

// Use the standard namespace for cleaner code in contests.
using namespace std;

int main() {
    // ---- 1. SETUP AND FAST I/O ----
    // This is a standard competitive programming optimization.
    // ios_base::sync_with_stdio(false) unties C++ streams from C streams.
    // cin.tie(NULL) prevents cin from flushing cout.
    // This makes input/output operations much faster, which is crucial for large inputs.
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);

    // ---- 2. INPUT & INITIALIZATION ----
    int n, q; // n: size of the grid, q: number of queries.
    cin >> n >> q; // Read n and q from the input.

    // We create a prefix sum array of size (n+1) x (n+1) to use 1-based indexing.
    // This simplifies the formulas and avoids out-of-bounds errors for coordinates like (i-1, j-1).
    // Initializing all values to 0 is important as it provides the base case for our calculations.
    // An 'int' is sufficient here since the maximum number of trees (1000*1000 = 1,000,000) fits.
    vector<vector<int>> prefix_sum(n + 1, vector<int>(n + 1, 0));

    // ---- 3. BUILDING THE PREFIX SUM ARRAY ----
    // Iterate from i=1 to n and j=1 to n, corresponding to the 1-based grid coordinates.
    for (int i = 1; i <= n; ++i) {
        for (int j = 1; j <= n; ++j) {
            char cell_char; // Variable to store the character for the current cell.
            cin >> cell_char; // Read the character ('.' or '*').

            // Convert the character to a numerical value. A tree '*' is 1, an empty square '.' is 0.
            int value = (cell_char == '*') ? 1 : 0;

            // This is the core formula to build the 2D prefix sum array.
            // It calculates the total number of trees in the rectangle from (1,1) to (i,j).
            prefix_sum[i][j] = value                         // The value (0 or 1) of the current cell.
                               + prefix_sum[i - 1][j]        // Add the number of trees in the rectangle directly above.
                               + prefix_sum[i][j - 1]        // Add the number of trees in the rectangle directly to the left.
                               - prefix_sum[i - 1][j - 1];   // The top-left region was counted twice, so we subtract it once.
        }
    }

    // ---- 4. PROCESSING QUERIES ----
    // Loop 'q' times to process all the queries.
    while (q--) {
        int y1, x1, y2, x2; // Coordinates of the query rectangle's top-left (y1, x1) and bottom-right (y2, x2) corners.
        cin >> y1 >> x1 >> y2 >> x2; // Read the four coordinate values for the current query.

        // This is the core formula to query the sum of a sub-rectangle in O(1) time.
        // It uses the precomputed values and the principle of inclusion-exclusion.
        int result = prefix_sum[y2][x2]                 // Total trees in the large rectangle from (1,1) to (y2,x2).
                     - prefix_sum[y1 - 1][x2]           // Subtract the unwanted trees in the rectangle above our target.
                     - prefix_sum[y2][x1 - 1]           // Subtract the unwanted trees in the rectangle to the left of our target.
                     + prefix_sum[y1 - 1][x1 - 1];      // Add back the top-left corner region's trees, as they were subtracted twice.

        // Print the final result for the current query. Using '\n' is faster than 'endl' in competitive programming.
        cout << result << "\n";
    }

    // ---- 5. END OF PROGRAM ----
    // A return value of 0 indicates that the program executed successfully.
    return 0;
}
```