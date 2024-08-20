# [Bipartite Graph](https://www.geeksforgeeks.org/problems/bipartite-graph/1)

![](https://badgen.net/badge/Level/Medium/yellow)

Given an adjacency list of a graph adj of V no. of vertices having 0 based index. Check whether the graph is bipartite or not. (coloured using two colours such that adjacent vertices are not of same colour).

### Approach Used :

-   Graph Coloring Using BFS/DFS:
    -   We can use either BFS or DFS to traverse the graph and try to color it. For simplicity, we'll use BFS here.
    -   We maintain a color array where each element can be -1 (uncolored), 0 (first color), or 1 (second color).
    -   Start from an uncolored node and assign it a color (say 0). Then, attempt to color all its adjacent nodes with the opposite color (1).
    -   If we find an adjacent node that is already colored with the same color, the graph is not bipartite.
    -   We repeat this process for all components of the graph since the graph may be disconnected.
-   Implementation:
    -   Traverse each vertex. If the vertex is uncolored, start a BFS from that vertex to check the bipartite condition for that component.

### Code (C++)

```cpp
class Solution {
public:
    bool bfsCheck(int src, vector<int> &color, vector<int> adj[]) {
        queue<int> q;
        q.push(src);
        color[src] = 0;  // Start coloring with color 0

        while (!q.empty()) {
            int node = q.front();
            q.pop();

            // Check all adjacent vertices
            for (int neighbor : adj[node]) {
                // If the neighbor is uncolored, color it with the opposite color
                if (color[neighbor] == -1) {
                    color[neighbor] = 1 - color[node];
                    q.push(neighbor);
                }
                // If the neighbor has the same color as the current node, it's not bipartite
                else if (color[neighbor] == color[node]) {
                    return false;
                }
            }
        }
        return true;
    }

    bool isBipartite(int V, vector<int> adj[]) {
        vector<int> color(V, -1); // Initialize all vertices as uncolored

        // Check for each component of the graph
        for (int i = 0; i < V; i++) {
            if (color[i] == -1) {
                // If the component starting at node i is not bipartite, return false
                if (!bfsCheck(i, color, adj)) {
                    return false;
                }
            }
        }
        return true; // If all components are bipartite, return true
    }
};
```

### Time Complexity:
- **O(V + E):**  where V is the number of vertices and E is the number of edges. This is because each vertex and edge is processed once.

### Space Complexity:
- **O(V):** for the color array and the BFS queue.

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>