# [Steps by Knight](https://www.geeksforgeeks.org/problems/steps-by-knight5927/1)

![](https://badgen.net/badge/Level/Medium/yellow)

Given a square chessboard, the initial position of Knight and position of a target. Find out the minimum steps a Knight will take to reach the target position.

Note:
The initial and the target position coordinates of Knight have been given according to 1-base indexing.

### Approach Used :

-   Possible Moves: A Knight on a chessboard can move in 8 possible directions. For each position (x, y), the possible moves are:
    -   (x + 2, y + 1), (x + 2, y - 1), (x - 2, y + 1), (x - 2, y - 1)
    -   (x + 1, y + 2), (x + 1, y - 2), (x - 1, y + 2), (x - 1, y - 2)
-   BFS Initialization:
    -   Start from the Knight's initial position.
    -   Use a queue to explore each possible position the Knight can move to, layer by layer.
    -   Keep track of visited positions to avoid cycles and redundant work.
-   Target Check:
    -   If the Knight reaches the target position, return the number of moves made.
-   Edge Cases:
    -   If the Knight is already at the target position, return 0 since no moves are needed.

### Code (C++)

```cpp
class Solution {
public:
    // Utility function to check if a position is inside the chessboard and not visited
    bool isValid(int x, int y, int N, vector<vector<bool>>& visited) {
        return (x >= 1 && x <= N && y >= 1 && y <= N && !visited[x][y]);
    }
    
    // Function to find out minimum steps Knight needs to reach target position.
    int minStepToReachTarget(vector<int>& KnightPos, vector<int>& TargetPos, int N) {
        // Directions a Knight can move
        int dx[] = {2, 2, -2, -2, 1, 1, -1, -1};
        int dy[] = {1, -1, 1, -1, 2, -2, 2, -2};
        
        // Queue for BFS
        queue<pair<pair<int, int>, int>> q; // ((x, y), steps)
        
        // Visited array
        vector<vector<bool>> visited(N + 1, vector<bool>(N + 1, false));
        
        // Starting position
        int startX = KnightPos[0];
        int startY = KnightPos[1];
        q.push({{startX, startY}, 0});
        visited[startX][startY] = true;
        
        // Target position
        int targetX = TargetPos[0];
        int targetY = TargetPos[1];
        
        // BFS
        while (!q.empty()) {
            auto curr = q.front();
            q.pop();
            
            int x = curr.first.first;
            int y = curr.first.second;
            int steps = curr.second;
            
            // If the Knight reaches the target position
            if (x == targetX && y == targetY) {
                return steps;
            }
            
            // Explore all possible moves
            for (int i = 0; i < 8; i++) {
                int newX = x + dx[i];
                int newY = y + dy[i];
                
                if (isValid(newX, newY, N, visited)) {
                    visited[newX][newY] = true;
                    q.push({{newX, newY}, steps + 1});
                }
            }
        }
        
        // In case the Knight can't reach the target, though this shouldn't happen as the board is finite and bounded.
        return -1;
    }
};
```

### Time Complexity:
- **O(n^2):** where n is the size of the chessboard. In the worst case, we may need to visit all positions on the board.

### Space Complexity:
- **O(n^2):** for storing the visited positions and the BFS queue.

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>