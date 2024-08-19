# [Rotten Oranges](https://www.geeksforgeeks.org/problems/rotten-oranges2536/1)

![](https://badgen.net/badge/Level/Medium/yellow)

Given a grid of dimension nxm where each cell in the grid can have values 0, 1 or 2 which has the following meaning:
0 : Empty cell
1 : Cells have fresh oranges
2 : Cells have rotten oranges

We have to determine what is the earliest time after which all the oranges are rotten. A rotten orange at index [i,j] can rot other fresh orange at indexes [i-1,j], [i+1,j], [i,j-1], [i,j+1] (up, down, left and right) in unit time. 

### Approach Used :

-   To solve the problem of determining the earliest time after which all the oranges are rotten, we can use the Breadth-First Search (BFS) algorithm. The idea is to start BFS from all the initially rotten oranges simultaneously and spread the rotting process in all four possible directions (up, down, left, right). The BFS ensures that we calculate the minimum time for all fresh oranges to become rotten.

### Code (C++)

```cpp
class Solution {
public:
    // Function to find minimum time required to rot all oranges.
    int orangesRotting(vector<vector<int>>& grid) {
        int n = grid.size();
        int m = grid[0].size();
        
        queue<pair<int, int>> q; // Queue to store rotten oranges (x, y) coordinates.
        int freshOranges = 0;    // Count of fresh oranges.
        int time = 0;            // Time to rot all oranges.
        
        // Directions for moving in the grid: up, down, left, right.
        vector<pair<int, int>> directions = {{-1, 0}, {1, 0}, {0, -1}, {0, 1}};
        
        // Initialize the queue with all rotten oranges and count fresh oranges.
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                if (grid[i][j] == 2) {
                    q.push({i, j});
                } else if (grid[i][j] == 1) {
                    freshOranges++;
                }
            }
        }
        
        // Perform BFS to rot adjacent fresh oranges.
        while (!q.empty() && freshOranges > 0) {
            int size = q.size();
            for (int i = 0; i < size; i++) {
                pair<int,int> ref = q.front();
                int x  = ref.first , y = ref.second;
                q.pop();
                
                // Check all four possible directions.
                for (pair<int,int> d: directions) {
                    int newX = x + d.first;
                    int newY = y + d.second;
                    
                    // If the new position is within bounds and has a fresh orange.
                    if (newX >= 0 && newX < n && newY >= 0 && newY < m && grid[newX][newY] == 1) {
                        // Rot the fresh orange and push the new rotten orange into the queue.
                        grid[newX][newY] = 2;
                        q.push({newX, newY});
                        freshOranges--; // Decrease the count of fresh oranges.
                    }
                }
            }
            time++; // Increment time after each level of BFS.
        }
        
        // If there are still fresh oranges left, return -1. Otherwise, return time.
        return (freshOranges == 0) ? time : -1;
    }
};
```

### Time Complexity:
- **O(n * m):** where n and m are the dimensions of the grid. This is because we process each cell of the grid at most once.

### Space Complexity:
- **O(n * m):** in the worst case, for storing the positions of the oranges in the queue..

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>