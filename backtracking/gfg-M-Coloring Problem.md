# [M-Coloring Problem](https://www.geeksforgeeks.org/problems/m-coloring-problem-1587115620/1)

![](https://badgen.net/badge/Level/Medium/yellow)

Given an undirected graph and an integer M. The task is to determine if the graph can be colored with at most M colors such that no two adjacent vertices of the graph are colored with the same color. Here coloring of a graph means the assignment of colors to all vertices. Print 1 if it is possible to colour vertices and 0 otherwise.

### Approach Used :

-   Backtracking Function: Use a recursive function to try coloring each vertex.
    -   If all vertices are colored (node == n), return true.
    -   Try assigning each color (from 1 to m) to the current vertex.
    -   Check if the current color assignment is valid using isSafe.
    -   If valid, recurse to the next vertex.
    -   If not valid or if the recursive call returns false, backtrack by resetting the color of the current vertex.
-   Color Validation: Before coloring a vertex, ensure that no adjacent vertices have the same color.
-   Recursive Solution: If all vertices are colored successfully with the constraints, return true. Otherwise, backtrack.

### Code (C++)

```cpp
class Solution{
public:
    // Function to determine if graph can be coloured with at most M colours such
    // that no two adjacent vertices of graph are coloured with same colour.
    bool graphColoring(bool graph[101][101], int m, int n) {
        vector<int> colors(n, 0); // To store colors assigned to vertices
        return canColor(0, graph, colors, m, n);
    }
    
private:
    bool canColor(int node, bool graph[101][101], vector<int>& colors, int m, int n) {
        // If all nodes are colored, return true
        if (node == n) return true;
        
        // Try assigning each color from 1 to m
        for (int color = 1; color <= m; ++color) {
            if (isSafe(node, graph, colors, color, n)) {
                colors[node] = color; // Assign color
                if (canColor(node + 1, graph, colors, m, n)) return true; // Recurse
                colors[node] = 0; // Backtrack
            }
        }
        
        return false; // If no color can be assigned
    }
    
    bool isSafe(int node, bool graph[101][101], vector<int>& colors, int color, int n) {
        // Check if adjacent nodes have the same color
        for (int i = 0; i < n; ++i) {
            if (graph[node][i] && colors[i] == color) return false;
        }
        return true;
    }
};

```

### Time Complexity:
- **O(m<sup>n</sup>):** In the worst case, the algorithm tries m colors for each of the n vertices, leading to an exponential time complexity

### Space Complexity:
- **O(n):** The space complexity is primarily due to the recursion stack and the colors vector, both of which can go as deep as n.

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>