# [Maximum size rectangle binary sub-matrix with all 1s](https://www.geeksforgeeks.org/maximum-size-rectangle-binary-sub-matrix-1s/)

![](https://badgen.net/badge/Level/Medium/yellow)

Given a binary matrix, find the maximum size rectangle binary-sub-matrix with all 1’s. 

### Approach Used-1 (using histogram problem) :

-   Run a loop to traverse through the rows.
-   Now If the current row is not the first row then update the row as follows, if matrix[i][j] is not zero then matrix[i][j] = matrix[i-1][j] + matrix[i][j].
-   Find the maximum rectangular area under the histogram, consider the ith row as heights of bars of a histogram. This can be calculated as given in this article Largest Rectangular Area in a Histogram
-   Do the previous two steps for all rows and print the maximum area of all the rows.

### Code-1 (C++)

```cpp
// C++ program to find largest
// rectangle with all 1s
// in a binary matrix
#include <bits/stdc++.h>
using namespace std;

// Rows and columns in input matrix
#define R 4
#define C 4

// Finds the maximum area under 
// the histogram represented
// by histogram.  See below article for details.


int maxHist(int row[])
{
    // Create an empty stack. 
    // The stack holds indexes of
    // hist[] array/ The bars stored 
    // in stack are always
    // in increasing order of their heights.
    stack<int> result;

    int top_val; // Top of stack

    int max_area = 0; // Initialize max area in current
    // row (or histogram)

    int area = 0; // Initialize area with current top

    // Run through all bars of given histogram (or row)
    int i = 0;
    while (i < C) {
        // If this bar is higher than the bar on top stack,
        // push it to stack
        if (result.empty() || row[result.top()] <= row[i])
            result.push(i++);

        else {
            // If this bar is lower than top of stack, then
            // calculate area of rectangle with stack top as
            // the smallest (or minimum height) bar. 'i' is
            // 'right index' for the top and element before
            // top in stack is 'left index'
            top_val = row[result.top()];
            result.pop();
            area = top_val * i;

            if (!result.empty())
                area = top_val * (i - result.top() - 1);
            max_area = max(area, max_area);
        }
    }

    // Now pop the remaining bars from stack and calculate
    // area with every popped bar as the smallest bar
    while (!result.empty()) {
        top_val = row[result.top()];
        result.pop();
        area = top_val * i;
        if (!result.empty())
            area = top_val * (i - result.top() - 1);

        max_area = max(area, max_area);
    }
    return max_area;
}

// Returns area of the largest rectangle with all 1s in
// A[][]
int maxRectangle(int A[][C])
{
    // Calculate area for first row and initialize it as
    // result
    int result = maxHist(A[0]);

    // iterate over row to find maximum rectangular area
    // considering each row as histogram
    for (int i = 1; i < R; i++) {

        for (int j = 0; j < C; j++)

            // if A[i][j] is 1 then add A[i -1][j]
            if (A[i][j])
                A[i][j] += A[i - 1][j];

        // Update result if area with current row (as last
        // row) of rectangle) is more
        result = max(result, maxHist(A[i]));
    }

    return result;
}

// Driver code
int main()
{
    int A[][C] = {
        { 0, 1, 1, 0 },
        { 1, 1, 1, 1 },
        { 1, 1, 1, 1 },
        { 1, 1, 0, 0 },
    };

    cout << "Area of maximum rectangle is "
         << maxRectangle(A);

    return 0;
}

```

### Time Complexity:
- **O(R x C x C):** One traversal of the matrix is required, another is traversal of every column

### Space Complexity:
- **O(C):** Stack is required to store the columns

### Approach Used-2 (dynamic programming) :

-   For each cell, use dynamic programming to get the maximum height of the rectangle that ends 
at the cell. To get the maximum width of the rectangle with the cell as its bottom-right corner, 
expand leftwards. To calculate the maximum area for each cell, expand leftward. 
Keep track of the maximum

    -   Create two auxiliary matrices.
    -   One to store the maximum height of consecutive 1s above a cell
    -   One to store the maximum height of consecutive 1s below a cell
    -   For each cell in the matrix calculate the maximum area by considering the heights stored in the auxiliary matrices
    -   Keep track of the maximum area found

### Code (C++)

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int maximalRectangle(vector<vector<char>>& matrix) {
    if (matrix.empty() || matrix[0].empty()) {
        return 0;
    }

    int m = matrix.size();
    int n = matrix[0].size();
    vector<int> left(n, 0);
    vector<int> right(n, n);
    vector<int> height(n, 0);
    int maxArea = 0;

    for (const auto& row : matrix) {
        int curLeft = 0, curRight = n;

        // Update height array
        for (int j = 0; j < n; j++) {
            if (row[j] == '1') {
                height[j]++;
            } else {
                height[j] = 0;
            }
        }

        // Update left boundary array
        for (int j = 0; j < n; j++) {
            if (row[j] == '1') {
                left[j] = max(left[j], curLeft);
            } else {
                left[j] = 0;
                curLeft = j + 1;
            }
        }

        // Update right boundary array
        for (int j = n - 1; j >= 0; j--) {
            if (row[j] == '1') {
                right[j] = min(right[j], curRight);
            } else {
                right[j] = n;
                curRight = j;
            }
        }

        // Calculate maximum area for each cell
        for (int j = 0; j < n; j++) {
            maxArea = max(maxArea, (right[j] - left[j]) * height[j]);
        }
    }

    return maxArea;
}

int main() {
    vector<vector<char>> matrix1 = {
        {'0', '1', '1', '0'},
        {'1', '1', '1', '1'},
        {'1', '1', '1', '1'},
        {'1', '1', '0', '0'}
    };

    cout << maximalRectangle(matrix1) << endl;

    return 0;
}

```

### Time Complexity:
- **O(m * n):** where m is the number of rows & n is the number of columns in the input matrix.

### Space Complexity:
- **O(n):** dp array
### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>