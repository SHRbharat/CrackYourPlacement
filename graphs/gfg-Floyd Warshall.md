# [Floyd Warshall](https://www.geeksforgeeks.org/problems/implementing-floyd-warshall2042/1)

![](https://badgen.net/badge/Level/Medium/yellow)

The problem is to find the shortest distances between every pair of vertices in a given edge-weighted directed graph. The graph is represented as an adjacency matrix of size n*n. Matrix[i][j] denotes the weight of the edge from i to j. If Matrix[i][j]=-1, it means there is no edge from i to j.
Note : Modify the distances for every pair in-place.

### Approach Used :

-   Initialization:
    -   Initialize the distance from a vertex to itself as 0.
    -   For each edge in the graph, set the distance between the two vertices connected by the edge to the edge's weight.
    -   If there is no direct edge between two vertices, initialize the distance as infinity (INF), or leave it as it is (e.g., when the value is -1).
-   Algorithm:
    -   For each intermediate vertex k, and for each pair of vertices (i, j), update the distance matrix[i][j] as:
        *matrix[i][j]=min(matrix[i][j],matrix[i][k]+matrix[k][j])*
    -   This update checks if a path from i to j through k is shorter than the current known path from i to j.

### Code (C++)

```cpp
class Solution {
  public:
    void shortest_distance(vector<vector<int>>& matrix) {
        int n = matrix.size();
        int INF = 1e9; // Use a large value to represent infinity
        
        // Step 1: Convert all -1 values to a large number (INF) except the diagonal
        for (int i = 0; i < n; ++i) {
            for (int j = 0; j < n; ++j) {
                if (matrix[i][j] == -1 && i != j) {
                    matrix[i][j] = INF;
                }
            }
        }
        
        // Step 2: Apply Floyd-Warshall Algorithm
        for (int k = 0; k < n; ++k) {
            for (int i = 0; i < n; ++i) {
                for (int j = 0; j < n; ++j) {
                    if (matrix[i][k] < INF && matrix[k][j] < INF) {
                        matrix[i][j] = min(matrix[i][j], matrix[i][k] + matrix[k][j]);
                    }
                }
            }
        }
        
        // Step 3: Convert back all values that are still INF to -1 (indicating no path)
        for (int i = 0; i < n; ++i) {
            for (int j = 0; j < n; ++j) {
                if (matrix[i][j] == INF) {
                    matrix[i][j] = -1;
                }
            }
        }
    }
};

```

### Time Complexity:
- **O(n^3):** where n is the number of vertices. This is due to the three nested loops iterating over all pairs of vertices and an intermediate vertex.

### Space Complexity:
- **O(1):** additional space, since the algorithm works in-place on the input matrix.

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>