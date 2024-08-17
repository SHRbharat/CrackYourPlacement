# [DFS of Graph](https://www.geeksforgeeks.org/problems/depth-first-traversal-for-a-graph/1)

![](https://badgen.net/badge/Level/Easy/green)

You are given a connected undirected graph. Perform a Depth First Traversal of the graph.
Note: Use the recursive approach to find the DFS traversal of the graph starting from the 0th vertex from left to right according to the graph.

### Approach Used :

-   Maintain a visited array to keep track of the visited nodes.
-   Create a helper recursive function to visit the nodes.
-   Start from the 0th vertex and recursively visit its neighbors in depth-first order, ensuring that no node is revisited.
-   Store the visited nodes in a result vector, which will hold the DFS traversal sequence.


### Code (C++)

```cpp
class Solution {
public:
    // Helper function to perform DFS recursively.
    void dfsHelper(int node, std::vector<int>& visited, std::vector<int>& dfsResult, std::vector<int> adj[]) {
        // Mark the current node as visited and store it in the result.
        visited[node] = true;
        dfsResult.push_back(node);
        
        // Recursively visit all the adjacent vertices of the current node.
        for (int adjacent : adj[node]) {
            if (!visited[adjacent]) {
                dfsHelper(adjacent, visited, dfsResult, adj);
            }
        }
    }
    
    // Function to return a list containing the DFS traversal of the graph.
    std::vector<int> dfsOfGraph(int V, std::vector<int> adj[]) {
        // Vector to store the DFS traversal result.
        std::vector<int> dfsResult;
        
        // Array to keep track of visited nodes.
        std::vector<int> visited(V, false);
        
        // Start the DFS from the 0th vertex.
        dfsHelper(0, visited, dfsResult, adj);
        
        return dfsResult;
    }
};


//using stack
class Solution {
public:
    // Function to return a list containing the DFS traversal of the graph.
    std::vector<int> dfsOfGraph(int V, std::vector<int> adj[]) {
        // Vector to store the DFS traversal result.
        std::vector<int> dfsResult;
        
        // Array to keep track of visited nodes.
        std::vector<bool> visited(V, false);
        
        // Stack for DFS iteration.
        std::stack<int> st;
        
        // Start the DFS from the 0th vertex.
        st.push(0);
        
        while (!st.empty()) {
            // Pop the top node from the stack.
            int node = st.top();
            st.pop();
            
            // If the node has not been visited, process it.
            if (!visited[node]) {
                // Mark the node as visited.
                visited[node] = true;
                
                // Store the node in the result.
                dfsResult.push_back(node);
            }

            // Visit all the adjacent vertices of the current node.
            // Push them onto the stack in reverse order so that
            // the leftmost vertices are processed first (LIFO).
            for (auto it = adj[node].rbegin(); it != adj[node].rend(); ++it) {
                if (!visited[*it]) {
                    st.push(*it);
                }
            }
        }
        
        return dfsResult;
    }
};
```

### Time Complexity:
- **O(v + e):** This is because each vertex and edge is processed at most once.

### Space Complexity:
- **O(v):** due to the recursion stack and the visited array..


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>