# [Strongly Connected Components (Kosaraju's Algo)](https://www.geeksforgeeks.org/problems/strongly-connected-components-kosarajus-algo/1)

![](https://badgen.net/badge/Level/Medium/yellow)

Given a Directed Graph with V vertices (Numbered from 0 to V-1) and E edges, Find the number of strongly connected components in the graph.

### Approach Used :

-   Perform DFS on the original graph, storing the nodes in a stack based on their finishing times. This step orders the nodes for the subsequent DFS on the transpose graph.
-   Create a transpose (reversed) graph where all edges are reversed.
-   Perform DFS on the transpose graph in the order determined by the stack from Step 1. Each DFS in this phase represents one strongly connected component (SCC).
-   Count the number of DFS calls made in Step 3, as each call corresponds to an SCC.

### Code (C++)

```cpp
class Solution
{
    void dfs1(int node, vector<vector<int>>& adj, vector<bool>& visited, stack<int>& st) {
        visited[node] = true;
        for (int neighbor : adj[node]) {
            if (!visited[neighbor]) {
                dfs1(neighbor, adj, visited, st);
            }
        }
        st.push(node);
    }

    void dfs2(int node, vector<vector<int>>& transposeAdj, vector<bool>& visited) {
        visited[node] = true;
        for (int neighbor : transposeAdj[node]) {
            if (!visited[neighbor]) {
                dfs2(neighbor, transposeAdj, visited);
            }
        }
    }

public:
    int kosaraju(int V, vector<vector<int>>& adj)
    {
        // Step 1: Do DFS and push nodes onto the stack in the order of completion time
        stack<int> st;
        vector<bool> visited(V, false);
        for (int i = 0; i < V; ++i) {
            if (!visited[i]) {
                dfs1(i, adj, visited, st);
            }
        }

        // Step 2: Create the transpose (reverse) of the graph
        vector<vector<int>> transposeAdj(V);
        for (int i = 0; i < V; ++i) {
            for (int neighbor : adj[i]) {
                transposeAdj[neighbor].push_back(i);
            }
        }

        // Step 3: Do DFS on the transpose graph in the order defined by the stack
        fill(visited.begin(), visited.end(), false);
        int sccCount = 0;
        while (!st.empty()) {
            int node = st.top();
            st.pop();
            if (!visited[node]) {
                dfs2(node, transposeAdj, visited);
                sccCount++;
            }
        }

        return sccCount;
    }
};

```

### Time Complexity:
- **O(V + E):** where V is the number of vertices and E is the number of edges. This is because each vertex and edge is processed a constant number of times.

### Space Complexity:
- **O(V + E):** for storing the graph, transpose graph, and auxiliary data structures like the stack and visited array.

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>