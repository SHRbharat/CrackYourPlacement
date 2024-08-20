# [Travelling Salesman Problem using Dynamic Programming](https://www.geeksforgeeks.org/travelling-salesman-problem-using-dynamic-programming/)

![](https://badgen.net/badge/Level/Medium/yellow)

Given a set of cities and the distance between every pair of cities, the problem is to find the shortest possible route that visits every city exactly once and returns to the starting point. Note the difference between Hamiltonian Cycle and TSP. The Hamiltonian cycle problem is to find if there exists a tour that visits every city exactly once. Here we know that Hamiltonian Tour exists (because the graph is complete) and in fact, many such tours exist, the problem is to find a minimum weight Hamiltonian Cycle. 

### Approach Used :

-   Dynamic Programming with Bitmasking:
    -   Bitmasking is used to keep track of the cities that have been visited. A bitmask is an integer where the i-th bit represents whether the i-th city has been visited.
    -   Dynamic Programming (DP) is used to store the results of sub-problems to avoid recomputation. The DP state is represented as dp[i][mask], where i is the current city and mask is the bitmask representing the set of visited cities.
-   Recursive Function fun(int i, int mask):
    -   Base Case: When only the starting city and one other city are left in the mask, return the distance from the starting city to the current city.
    -   Recursive Case: For each city j that has been visited (j is set in mask), calculate the minimum cost to reach the current city i from j by visiting all other cities in the mask and then returning to the starting city.
-   Final Calculation:
    -   The main function iterates over all possible cities as the last visited city and computes the minimum cost to complete the tour by visiting all cities and returning to the starting city.

### Code (C++)

```cpp
// there are four nodes in example graph (graph is 1-based)
const int n = 4;
// give appropriate maximum to avoid overflow
const int MAX = 1000000;
 
// dist[i][j] represents shortest distance to go from i to j
// this matrix can be calculated for any given graph using
// all-pair shortest path algorithms
int dist[n + 1][n + 1] = {
    { 0, 0, 0, 0, 0 },    { 0, 0, 10, 15, 20 },
    { 0, 10, 0, 25, 25 }, { 0, 15, 25, 0, 30 },
    { 0, 20, 25, 30, 0 },
};
 
// memoization for top down recursion
int memo[n + 1][1 << (n + 1)];
 
int fun(int i, int mask)
{
    // base case
    // if only ith bit and 1st bit is set in our mask,
    // it implies we have visited all other nodes already
    if (mask == ((1 << i) | 3))
        return dist[1][i];
    // memoization
    if (memo[i][mask] != 0)
        return memo[i][mask];
 
    int res = MAX; // result of this sub-problem
 
    // we have to travel all nodes j in mask and end the
    // path at ith node so for every node j in mask,
    // recursively calculate cost of travelling all nodes in
    // mask except i and then travel back from node j to
    // node i taking the shortest path take the minimum of
    // all possible j nodes
 
    for (int j = 1; j <= n; j++)
        if ((mask & (1 << j)) && j != i && j != 1)
            res = std::min(res, fun(j, mask & (~(1 << i)))
                                    + dist[j][i]);
    return memo[i][mask] = res;
}
// Driver program to test above logic
int main()
{
    int ans = MAX;
    for (int i = 1; i <= n; i++)
        // try to go from node 1 visiting all nodes in
        // between to i then return from i taking the
        // shortest route to 1
        ans = std::min(ans, fun(i, (1 << (n + 1)) - 1)
                                + dist[i][1]);
 
    printf("The cost of most efficient tour = %d", ans);
 
    return 0;
}
```

### Time Complexity:
- **O(n<sup>2</sup> * 2<sup>n</sup>):** where O(n* 2^n) are maximum number of unique subproblems/states and O(n) for transition (through for loop as in code) in every states.

### Space Complexity:
- **O(n * 2<sup>n</sup>):** where n is number of Nodes/Cities here.

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>