# [Prerequisite Tasks](https://www.geeksforgeeks.org/problems/prerequisite-tasks/1)

![](https://badgen.net/badge/Level/Medium/yellow)

There are a total of N tasks, labeled from 0 to N-1. Some tasks may have prerequisites, for example to do task 0 you have to first complete task 1, which is expressed as a pair: [0, 1]
Given the total number of tasks N and a list of prerequisite pairs P, find if it is possible to finish all tasks.

### Approach Used :

-   Graph Representation:
    -   Each task is a node.
    -   Each prerequisite pair [a, b] represents a directed edge from b to a (i.e., b must be completed before a).
-   Cycle Detection:
    -   If the graph has a cycle, it's impossible to complete all tasks because you would encounter a circular dependency.
    -   We can use either Depth-First Search (DFS) with a recursion stack or Kahn's algorithm (a variant of BFS for topological sorting) to detect cycles.

### Code (C++)

```cpp
class Solution {
public:
    bool isPossible(int N, int P, vector<pair<int, int>>& prerequisites) {
        vector<vector<int>> adj(N);
        vector<int> inDegree(N, 0);
        
        // Build the graph
        for (auto& prerequisite : prerequisites) {
            int u = prerequisite.second;
            int v = prerequisite.first;
            adj[u].push_back(v);
            inDegree[v]++;
        }
        
        queue<int> q;
        
        // Push all nodes with in-degree 0
        for (int i = 0; i < N; i++) {
            if (inDegree[i] == 0) {
                q.push(i);
            }
        }
        
        int count = 0;
        
        // Kahn's Algorithm for Topological Sorting
        while (!q.empty()) {
            int node = q.front();
            q.pop();
            count++;
            
            for (int neighbor : adj[node]) {
                inDegree[neighbor]--;
                if (inDegree[neighbor] == 0) {
                    q.push(neighbor);
                }
            }
        }
        
        // If count equals the number of nodes, all tasks can be completed
        return count == N;
    }
};

```

### Time Complexity:
- **O(N + P):** where N is the number of tasks and P is the number of prerequisite pairs. This accounts for building the graph and performing the BFS.

### Space Complexity:
- **O(N + P):** for storing the adjacency list and the inDegree array.

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>