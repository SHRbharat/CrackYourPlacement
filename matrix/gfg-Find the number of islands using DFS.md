# [Find the number of islands using DFS](https://www.geeksforgeeks.org/find-the-number-of-islands-using-dfs/)

![](https://badgen.net/badge/Level/Medium/yellow)

Given a binary 2D matrix, find the number of islands. A group of connected 1s forms an island.

### Approach Used :

-   Initialize count = 0, to store the answer.
-   For each cell of the input matrix check if the value of the current cell is 1 :
    -   Increment the count by 1 and call for DFS:
        -   if the cell exceeds the boundary or the value at the current cell is 0, return
        -   Update the value at the current cell as 0, Call DFS on the neighbor recursively
-   Return count as the final answer.

### Code (C++)

```cpp
// C++Program to count islands in boolean 2D matrix
#include <bits/stdc++.h>
using namespace std;

// A utility function to do DFS for a 2D
//  boolean matrix. It only considers
// the 8 neighbours as adjacent vertices
void DFS(vector<vector<int> >& M, int i, int j, int ROW,
         int COL)
{
    // Base condition
    // if i less than 0 or j less than 0 or i greater than
    // ROW-1 or j greater than COL-  or if M[i][j] != 1 then
    // we will simply return
    if (i < 0 || j < 0 || i > (ROW - 1) || j > (COL - 1)
        || M[i][j] != 1) {
        return;
    }

    if (M[i][j] == 1) {
        M[i][j] = 0;
        DFS(M, i + 1, j, ROW, COL); // right side traversal
        DFS(M, i - 1, j, ROW, COL); // left side traversal
        DFS(M, i, j + 1, ROW, COL); // upward side traversal
        DFS(M, i, j - 1, ROW,
            COL); // downward side traversal
        DFS(M, i + 1, j + 1, ROW,
            COL); // upward-right side traversal
        DFS(M, i - 1, j - 1, ROW,
            COL); // downward-left side traversal
        DFS(M, i + 1, j - 1, ROW,
            COL); // downward-right side traversal
        DFS(M, i - 1, j + 1, ROW,
            COL); // upward-left side traversal
    }
}

int countIslands(vector<vector<int> >& M)
{
    int ROW = M.size();
    int COL = M[0].size();
    int count = 0;
    for (int i = 0; i < ROW; i++) {
        for (int j = 0; j < COL; j++) {
            if (M[i][j] == 1) {
                count++;
                DFS(M, i, j, ROW, COL); // traversal starts
                                        // from current cell
            }
        }
    }
    return count;
}

// Driver Code
int main()
{
    vector<vector<int> > M = { { 1, 1, 0, 0, 0 },
                               { 0, 1, 0, 0, 1 },
                               { 1, 0, 0, 1, 1 },
                               { 0, 0, 0, 0, 0 },
                               { 1, 0, 1, 0, 1 } };

    cout << "Number of islands is: " << countIslands(M);
    return 0;
}

// This code is contributed by ajaymakvana.
//    Code improved by Animesh Singh

```

### Time Complexity:
- **O(ROW x COL):** 

### Space Complexity:
- **O(ROW x COL):** as to do DFS we need extra auxiliary stack space.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>