# [Minimum Spanning Tree](https://www.geeksforgeeks.org/problems/minimum-spanning-tree/1)

![](https://badgen.net/badge/Level/Medium/yellow)

Given a weighted, undirected, and connected graph with V vertices and E edges, your task is to find the sum of the weights of the edges in the Minimum Spanning Tree (MST) of the graph. The graph is represented by an adjacency list, where each element adj[i] is a vector containing vector of integers. Each vector represents an edge, with the first integer denoting the endpoint of the edge and the second integer denoting the weight of the edge.

### Approach Used :

-   Prim's Algorithm:
    -   Start with an arbitrary node, include it in the MST, and then repeatedly add the smallest edge that connects a vertex in the MST to a vertex outside the MST.
    -   Use a priority queue (min-heap) to select the minimum weight edge at each step.
    -   Keep track of visited nodes to avoid cycles.
-   Graph Representation:
    -   The graph is given as an adjacency list where adj[i] contains a list of pairs, with each pair representing an edge (end_vertex, weight).

### Code (C++)

```cpp
class Solution
{
	public:
	// Function to find sum of weights of edges of the Minimum Spanning Tree.
    int spanningTree(int V, vector<vector<int>> adj[])
    {
        // Min-heap to store (weight, vertex) pairs
        priority_queue<pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>>> minHeap;
        
        // To keep track of vertices included in MST
        vector<bool> inMST(V, false);
        
        // Start with vertex 0, weight 0
        minHeap.push({0, 0});
        int mstWeight = 0;
        
        while (!minHeap.empty()) {
            // Choose the edge with minimum weight
            int weight = minHeap.top().first;
            int u = minHeap.top().second;
            minHeap.pop();
            
            // If the vertex is already included in MST, continue
            if (inMST[u]) continue;
            
            // Include the vertex in MST
            inMST[u] = true;
            mstWeight += weight;
            
            // Explore the neighbors of the vertex
            for (auto &neighbor : adj[u]) {
                int v = neighbor[0];
                int w = neighbor[1];
                
                // If the neighbor is not in MST, push the edge to min-heap
                if (!inMST[v]) {
                    minHeap.push({w, v});
                }
            }
        }
        
        return mstWeight;
    }
};
```

### Time Complexity:
- **O((V+E)logV):**  because each vertex and edge is processed at most once and we use a priority queue.

### Space Complexity:
- **O(V+E):**  to store the graph, priority queue, and tracking structures.

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>