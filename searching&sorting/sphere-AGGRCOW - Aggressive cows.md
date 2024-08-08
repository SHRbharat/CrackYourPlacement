# [AGGRCOW - Aggressive cows](https://www.spoj.com/problems/AGGRCOW/)

![](https://badgen.net/badge/Level/Hard/red)

Farmer John has built a new long barn, with N (2 <= N <= 100,000) stalls. The stalls are located along a straight line at positions x1 ... xN (0 <= xi <= 1,000,000,000).

His C (2 <= C <= N) cows don't like this barn layout and become aggressive towards each other once put into a stall. To prevent the cows from hurting each other, FJ wants to assign the cows to the stalls, such that the minimum distance between any two of them is as large as possible. What is the largest minimum distance?

### Approach Used :

-Sort the Stall Positions
    - Sort the array of stall positions to allow efficient checking of possible distances.

-   Binary Search on Distance
    - Perform a binary search on the minimum distance between cows.
    - The search range is between `1` (smallest possible distance) and `x[N-1] - x[0]` (largest possible distance).

-   Greedy Placement
    - For each midpoint in the binary search, check if it's possible to place all `C` cows such that the minimum distance between any two cows is at least the midpoint.
    - Place the first cow in the first stall, and place each subsequent cow in the next available stall that is at least `midpoint` distance away.

-   Adjust Search Range
    - If placing the cows with the current midpoint distance is possible, increase the lower bound to try for a larger distance.
    - If not, reduce the upper bound to try smaller distances.

-   Return the Result
    - The largest midpoint value that allows placing all cows is the answer.

### Code (C++)

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

bool canPlaceCows(vector<int>& stalls, int C, int minDist) {
    int count = 1; // Place the first cow in the first stall
    int lastPosition = stalls[0];

    for (int i = 1; i < stalls.size(); i++) {
        if (stalls[i] - lastPosition >= minDist) {
            count++;
            lastPosition = stalls[i];
            if (count == C)
                return true;
        }
    }

    return count >= C;
}

int largestMinDist(vector<int>& stalls, int C) {
    sort(stalls.begin(), stalls.end());

    int low = 1; // minimum possible distance
    int high = stalls.back() - stalls[0]; // maximum possible distance
    int result = 0;

    while (low <= high) {
        int mid = low + (high - low) / 2;

        if (canPlaceCows(stalls, C, mid)) {
            result = mid; // This distance works, try for a larger one
            low = mid + 1;
        } else {
            high = mid - 1; // This distance doesn't work, try smaller
        }
    }

    return result;
}

int main() {
    int N, C;
    cin >> N >> C;
    vector<int> stalls(N);
    
    for (int i = 0; i < N; i++)
        cin >> stalls[i];

    cout << largestMinDist(stalls, C) << endl;

    return 0;
}

```

### Time Complexity:
- **O(N log N):** O(N log N) for sorting and O(log(max_distance) * N) for binary search.

### Space Complexity:
- **O(1):** no extra space is used.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>