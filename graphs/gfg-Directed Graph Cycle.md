# [Directed Graph Cycle](https://www.geeksforgeeks.org/problems/detect-cycle-in-a-directed-graph/1)

![](https://badgen.net/badge/Level/Medium/yellow)

Given a Directed Graph with V vertices (Numbered from 0 to V-1) and E edges, check whether it contains any cycle or not.

### Approach Used :

-   DFS with Recursion Stack:
    -   Maintain two arrays:
        -   visited[]: Tracks whether a node has been visited.
        -   recStack[]: Tracks nodes that are currently in the recursion stack (i.e., nodes that are part of the current DFS path).
    -   For each unvisited node, start a DFS traversal. If during the traversal you revisit a node that is already in the recursion stack, a cycle exists.
-   Handling All Components:
    -   Since the graph may be disconnected, ensure that you initiate DFS from every unvisited node.

### Code (C++)

```cpp
class Solution {
public:
    // Helper function for DFS
    bool dfs(int node, vector<int> adj[], vector<bool> &visited, vector<bool> &recStack) {
        visited[node] = true;
        recStack[node] = true;

        // Traverse all adjacent vertices
        for (int neighbor : adj[node]) {
            if (!visited[neighbor]) {
                // Recur for the next vertex
                if (dfs(neighbor, adj, visited, recStack)) {
                    return true;
                }
            } else if (recStack[neighbor]) {
                // If the adjacent vertex is in the recursion stack, there's a cycle
                return true;
            }
        }

        recStack[node] = false; // Remove the node from the recursion stack before backtracking
        return false;
    }

    // Function to detect cycle in a directed graph.
    bool isCyclic(int V, vector<int> adj[]) {
        vector<bool> visited(V, false);
        vector<bool> recStack(V, false);

        // Check each component of the graph
        for (int i = 0; i < V; i++) {
            if (!visited[i]) {
                if (dfs(i, adj, visited, recStack)) {
                    return true;
                }
            }
        }
        return false;
    }
};
```

### Time Complexity:
- **O(V + E):** where V is the number of vertices and E is the number of edges. Each node and edge is processed once.

### Space Complexity:
- **O(V):** for the visited and recStack arrays.

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>