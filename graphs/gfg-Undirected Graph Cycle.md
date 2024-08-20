# [Undirected Graph Cycle](https://www.geeksforgeeks.org/problems/detect-cycle-in-an-undirected-graph/1)

![](https://badgen.net/badge/Level/Medium/yellow)

Given an undirected graph with V vertices labelled from 0 to V-1 and E edges, check whether it contains any cycle or not. Graph is in the form of adjacency list where adj[i] contains all the nodes ith node is having edge with.

### Approach Used :

-   DFS Traversal:
    -   We start DFS from any unvisited node and explore the graph.
    -   During DFS, if we move to an adjacent node that has already been visited and is not the parent of the current node, then a cycle is detected.
    -   Since the graph might be disconnected, we must check each component of the graph by initiating DFS from each unvisited node.
-   Cycle Detection:
    -   Use a visited array to keep track of visited nodes.
    -   Use recursion to traverse the graph. If an adjacent node is visited and is not the parent, return true indicating a cycle.

### Code (C++)

```cpp
class Solution {
public:
    // Helper function for DFS
    bool dfs(int node, int parent, vector<int> &visited, vector<int> adj[]) {
        visited[node] = 1;  // Mark the current node as visited

        // Traverse all adjacent vertices
        for (int neighbor : adj[node]) {
            if (!visited[neighbor]) {
                // Recur for all the vertices adjacent to this vertex
                if (dfs(neighbor, node, visited, adj)) {
                    return true;
                }
            } 
            // If an adjacent vertex is visited and not the parent of the current vertex, a cycle is found
            else if (neighbor != parent) {
                return true;
            }
        }
        return false;
    }

    // Function to detect cycle in an undirected graph.
    bool isCycle(int V, vector<int> adj[]) {
        vector<int> visited(V, 0);  // Initialize all vertices as unvisited

        // Perform DFS from every vertex (in case of disconnected graph)
        for (int i = 0; i < V; i++) {
            if (!visited[i]) {  // If the vertex is not visited
                if (dfs(i, -1, visited, adj)) {  // -1 is used to indicate that the current node has no parent
                    return true;
                }
            }
        }
        return false;  // If no cycle is detected
    }
};
```

### Time Complexity:
- **O(V + E):** where V is the number of vertices and E is the number of edges. Each vertex and edge is processed once in the DFS.

### Space Complexity:
- **O(V):** for the visited array and the recursion stack.

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>