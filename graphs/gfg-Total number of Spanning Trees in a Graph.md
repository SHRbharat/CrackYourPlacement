# [Total number of Spanning Trees in a Graph](https://www.geeksforgeeks.org/total-number-spanning-trees-graph/)

![](https://badgen.net/badge/Level/Medium/yellow)

If a graph is a complete graph with n vertices, then total number of spanning trees is n(n-2) where n is the number of nodes in the graph. In complete graph, the task is equal to counting different labeled trees with n nodes for which have Cayley’s formula.

What if graph is not complete? 

### Approach Used :

-   Create Adjacency Matrix for the given graph. 
-   Replace all the diagonal elements with the degree of nodes. For eg. element at (1,1) position of adjacency matrix will be replaced by the degree of node 1, element at (2,2) position of adjacency matrix will be replaced by the degree of node 2, and so on. 
-   Replace all non-diagonal 1’s with -1. 
-   Calculate co-factor for any element. 
-   The cofactor that you get is the total number of spanning tree for that graph. 

### Code (C++)

```cpp
#define MAX 100 
#define MOD 1000000007 

// Matrix Multiplication 
void multiply(int A[MAX][MAX], int B[MAX][MAX], int C[MAX][MAX]) 
{ 
    for (int i = 0; i < MAX; i++) 
        for (int j = 0; j < MAX; j++) 
            for (int k = 0; k < MAX; k++) 
                C[i][j] = (C[i][j] + (A[i][k] * B[k][j])%MOD)%MOD;     
} 

// Function to find Nth power of A 
void power(int A[MAX][MAX], int N, int result[MAX][MAX]) 
{ 
    int temp[MAX][MAX]; 
    for (int i = 0; i < MAX; i++) 
        for (int j = 0; j < MAX; j++) 
            result[i][j] = (i == j); 

    while (N>0) 
    { 
        if (N%2 == 1) 
        { 
            multiply(A, result, temp); 
            for (int i=0; i<MAX; i++) 
                for (int j=0; j<MAX; j++) 
                    result[i][j] = temp[i][j]; 
        } 

        N = N/2; 
        multiply(A, A, temp); 
        for (int i=0; i<MAX; i++) 
            for (int j=0; j<MAX; j++) 
                A[i][j] = temp[i][j]; 
    } 
} 

// Function to find number of Spanning 
// Trees in a Graph using Matrix  
// Multiplication. 
int numOfSpanningTree(int graph[][MAX], int V) 
{ 
    int result[MAX][MAX] = {0}; 
    int temp[MAX][MAX] = {0}; 

    // Create a copy of graph as the 
    // Adjacency matrix will be changed 
    // during the process 
    for (int i = 0; i < V; i++) 
        for (int j = 0; j < V; j++) 
            temp[i][j] = graph[i][j]; 

    // Find (V-2)th power of Adjacency 
    // matrix 
    power(temp, V-2, result); 

    int ans = 0; 

    // Find sum of all elements in (V-2)th 
    // power 
    for (int i = 0; i < V; i++) 
        for (int j = 0; j < V; j++) 
            ans = (ans + result[i][j])%MOD; 

    return ans; 
} 



// Driver program 
int main() 
{ 
    // Let us create the following graph 
    // 2 <-> 3 
    // | | 
    // 0 <-1-> 1 
    int V = 4; // Number of vertices in graph 
    int E = 5; // Number of edges in graph 
    int graph[][MAX] = { 
                        {0, 1, 1, 1}, 
                        {1, 0, 1, 1}, 
                        {1, 1, 0, 1}, 
                        {1, 1, 1, 0} 
                    }; 

    cout << numOfSpanningTree(graph, V); 

    return 0; 
}
```

### Time Complexity:
- **O(V^3 * log N):** The given program uses the Matrix Chain Multiplication algorithm to find the number of spanning trees in a given graph. The algorithm works by computing the (V-2)th power of the adjacency matrix of the graph, where V is the number of vertices in the graph. The number of spanning trees in the graph is equal to the sum of all the entries in the resulting matrix.

The time complexity of the program is determined by the matrix multiplication and exponentiation operations. The matrix multiplication operation takes O(V^3) time, and it is performed N times, where N is the power to which the adjacency matrix is raised. Since N can be as large as V-2, the total time complexity of the program is O(V^3 * log N).

### Space Complexity:
- **O(V^2):** The space complexity of the program is determined by the size of the adjacency matrix and the result matrix. Since the matrices are of size VxV, the space complexity of the program is O(V^2). In addition, there are some temporary matrices created during the matrix multiplication and exponentiation operations, but they are of the same size as the input matrices and do not contribute significantly to the space complexity

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>