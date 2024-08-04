# [Given a matrix of ‘O’ and ‘X’, replace ‘O’ with ‘X’ if surrounded by ‘X’](https://www.geeksforgeeks.org/given-matrix-o-x-replace-o-x-surrounded-x/)

![](https://badgen.net/badge/Level/Medium/yellow)

Given a matrix where every element is either ‘O’ or ‘X’, replace ‘O’ with ‘X’ if surrounded by ‘X’. A ‘O’ (or a set of ‘O’) is considered to be surrounded by ‘X’ if there are ‘X’ at locations just below, just above, just left, and just right of it. 

### Approach Used :

-   Traverse the given matrix and replace all ‘O’ with a special character ‘-‘.
-   Traverse four edges of given matrix and call floodFill(‘-‘, ‘O’) for every ‘-‘ on edges. The remaining ‘-‘ are the characters that indicate ‘O’s (in the original matrix) to be replaced by ‘X’.
-   Traverse the matrix and replace all ‘-‘s with ‘X’s.

### Code (C++)

```cpp
#include<iostream>
using namespace std;
 
// Size of given matrix is M X N
#define M 6
#define N 6
 
 
// A recursive function to replace previous value 'prevV' at  '(x, y)'
// and all surrounding values of (x, y) with new value 'newV'.
void floodFillUtil(char mat[][N], int x, int y, char prevV, char newV)
{
    // Base cases
    if (x < 0 || x >= M || y < 0 || y >= N)
        return;
    if (mat[x][y] != prevV)
        return;
 
    // Replace the color at (x, y)
    mat[x][y] = newV;
 
    // Recur for north, east, south and west
    floodFillUtil(mat, x+1, y, prevV, newV);
    floodFillUtil(mat, x-1, y, prevV, newV);
    floodFillUtil(mat, x, y+1, prevV, newV);
    floodFillUtil(mat, x, y-1, prevV, newV);
}
 
// Returns size of maximum size subsquare matrix
// surrounded by 'X'
int replaceSurrounded(char mat[][N])
{
   // Step 1: Replace all 'O'  with '-'
   for (int i=0; i<M; i++)
      for (int j=0; j<N; j++)
          if (mat[i][j] == 'O')
             mat[i][j] = '-';
 
   // Call floodFill for all '-' lying on edges
   for (int i=0; i<M; i++)   // Left side
      if (mat[i][0] == '-')
        floodFillUtil(mat, i, 0, '-', 'O');
   for (int i=0; i<M; i++)  //  Right side
      if (mat[i][N-1] == '-')
        floodFillUtil(mat, i, N-1, '-', 'O');
   for (int i=0; i<N; i++)   // Top side
      if (mat[0][i] == '-')
        floodFillUtil(mat, 0, i, '-', 'O');
   for (int i=0; i<N; i++)  // Bottom side
      if (mat[M-1][i] == '-')
        floodFillUtil(mat, M-1, i, '-', 'O');
 
   // Step 3: Replace all '-' with 'X'
   for (int i=0; i<M; i++)
      for (int j=0; j<N; j++)
         if (mat[i][j] == '-')
             mat[i][j] = 'X';
 
}
 
// Driver program to test above function
int main()
{
    char mat[][N] =  {{'X', 'O', 'X', 'O', 'X', 'X'},
                     {'X', 'O', 'X', 'X', 'O', 'X'},
                     {'X', 'X', 'X', 'O', 'X', 'X'},
                     {'O', 'X', 'X', 'X', 'X', 'X'},
                     {'X', 'X', 'X', 'O', 'X', 'O'},
                     {'O', 'O', 'X', 'O', 'O', 'O'},
                    };
    replaceSurrounded(mat);
 
 
    for (int i=0; i<M; i++)
    {
      for (int j=0; j<N; j++)
          cout << mat[i][j] << " ";
      cout << endl;
    }
    return 0;
}
```

### Time Complexity:
- **O(MN):** every element of matrix is processed at most three times.

### Space Complexity:
- **O(MN):** as implicit stack is used due to recursive call


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>