# [Rat in a Maze Problem - I](https://www.geeksforgeeks.org/problems/rat-in-a-maze-problem/1)

![](https://badgen.net/badge/Level/Medium/yellow)

Consider a rat placed at (0, 0) in a square matrix mat of order n* n. It has to reach the destination at (n - 1, n - 1). Find all possible paths that the rat can take to reach from source to destination. The directions in which the rat can move are 'U'(up), 'D'(down), 'L' (left), 'R' (right). Value 0 at a cell in the matrix represents that it is blocked and rat cannot move to it while value 1 at a cell in the matrix represents that rat can be travel through it.
Note: In a path, no cell can be visited more than one time. If the source cell is 0, the rat cannot move to any other cell. In case of no path, return an empty list. The driver will output "-1" automatically.

### Approach Used :

-   Base Conditions:
    -   If the starting cell (0, 0) is blocked (i.e., mat[0][0] == 0), return an empty list as no paths are possible.
    -   Similarly, if the destination cell (n-1, n-1) is blocked, return an empty list.
-   DFS Traversal:
    -   Start from the top-left corner (0, 0) and try moving in all possible directions: D (down), U (up), L (left), R (right).
    -   Use a visited matrix to mark cells as visited during the current path to avoid cycles.
    -   If a valid path reaches the destination (n-1, n-1), add it to the list of paths.
-   Backtracking:
    -   After exploring a path from a cell, backtrack by unmarking it as visited, so it can be part of other paths.

### Code (C++)

```cpp
class Solution {
public:
    void dfs(vector<vector<int>>& mat, int x, int y, int n, string path, vector<string>& paths, vector<vector<int>>& visited) {
        // Base case: If destination is reached
        if (x == n-1 && y == n-1) {
            paths.push_back(path);
            return;
        }

        // Mark the current cell as visited
        visited[x][y] = 1;

        // Try moving Down
        if (x + 1 < n && !visited[x + 1][y] && mat[x + 1][y] == 1) {
            dfs(mat, x + 1, y, n, path + 'D', paths, visited);
        }
        // Try moving Left
        if (y - 1 >= 0 && !visited[x][y - 1] && mat[x][y - 1] == 1) {
            dfs(mat, x, y - 1, n, path + 'L', paths, visited);
        }
        // Try moving Right
        if (y + 1 < n && !visited[x][y + 1] && mat[x][y + 1] == 1) {
            dfs(mat, x, y + 1, n, path + 'R', paths, visited);
        }
        // Try moving Up
        if (x - 1 >= 0 && !visited[x - 1][y] && mat[x - 1][y] == 1) {
            dfs(mat, x - 1, y, n, path + 'U', paths, visited);
        }

        // Backtrack and unmark the current cell as visited
        visited[x][y] = 0;
    }

    vector<string> findPath(vector<vector<int>>& mat) {
        vector<string> paths;
        int n = mat.size();

        // If the start or end is blocked, return empty paths
        if (mat[0][0] == 0 || mat[n-1][n-1] == 0) {
            return paths;
        }

        vector<vector<int>> visited(n, vector<int>(n, 0));
        dfs(mat, 0, 0, n, "", paths, visited);
        return paths;
    }
};
```

### Time Complexity:
- **O(4^(n*n)):**  in the worst case since we may potentially explore every possible path. However, pruning occurs because we only explore valid moves.

### Space Complexity:
- **O(n*n):** for the recursion stack and the visited matrix.

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>