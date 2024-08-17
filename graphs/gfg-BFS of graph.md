# [BFS of graph](https://www.geeksforgeeks.org/problems/bfs-traversal-of-graph/1)

![](https://badgen.net/badge/Level/Easy/green)

Given a directed graph. The task is to do Breadth First Traversal of this graph starting from 0.
Note: One can move from node u to node v only if there's an edge from u to v. Find the BFS traversal of the graph starting from the 0th vertex, from left to right according to the input graph. Also, you should only take nodes directly or indirectly connected from Node 0 in consideration.

### Approach Used :

-   Initialize a queue to help with the BFS traversal.
-   Use a boolean array to keep track of visited nodes so that you don't visit the same node more than once.
-   Start from the 0th vertex, mark it as visited, and push it into the queue.
-   While the queue is not empty:
    -   Dequeue the front node from the queue.
    -   Append it to the BFS result list.
    -   For every adjacent vertex of the dequeued node, if it has not been visited yet:
        -   Mark it as visited.
        -   Enqueue it.

### Code (C++)

```cpp
class Solution {
public:
    // Function to return Breadth First Traversal of the given graph.
    std::vector<int> bfsOfGraph(int V, std::vector<int> adj[]) {
        // Vector to store the BFS traversal result.
        std::vector<int> bfsResult;
        
        // Array to keep track of visited nodes.
        std::vector<bool> visited(V, false);
        
        // Queue for BFS.
        std::queue<int> q;
        
        // Start with the 0th node.
        visited[0] = true;
        q.push(0);
        
        while (!q.empty()) {
            // Dequeue a vertex from the queue.
            int node = q.front();
            q.pop();
            
            // Store the node in the result.
            bfsResult.push_back(node);
            
            // Get all adjacent vertices of the dequeued node.
            for (int i : adj[node]) {
                if (!visited[i]) {
                    visited[i] = true;
                    q.push(i);
                }
            }
        }
        
        return bfsResult;
    }
};
```

### Time Complexity:
- **O(v + e):** because every vertex and every edge will be processed at most once.

### Space Complexity:
- **O(v):**  for storing the visited nodes and the queue..


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>