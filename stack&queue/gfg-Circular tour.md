# [Circular tour](https://www.geeksforgeeks.org/problems/circular-tour-1587115620/1)

![](https://badgen.net/badge/Level/Medium/yellow)

Suppose there is a circle. There are N petrol pumps on that circle. You will be given two sets of data.
1. The amount of petrol that every petrol pump has.
2. Distance from that petrol pump to the next petrol pump.
Find a starting point where the truck can start to get through the complete circle without exhausting its petrol in between.
Note :  Assume for 1 litre petrol, the truck can go 1 unit of distance.
### Approach Used :

-   To determine this, we can use a greedy algorithm that efficiently finds the starting point by keeping track of the cumulative petrol and distance.
-   Algorithm:
    -   Traverse the petrol pumps while keeping a cumulative sum of the petrol and the distance.
    -   If at any point the cumulative petrol is less than the cumulative distance, it means that the current starting point cannot reach the next petrol pump. Thus, you should update the starting point to the next petrol pump and reset the cumulative sums.
    -   At the end of the traversal, if the total petrol is greater than or equal to the total distance, then a valid starting point exists.
-   Steps:
    -   Calculate the total amount of petrol and the total distance.
    -   Traverse the petrol pumps and update the cumulative petrol and distance.
    -   If at any point, the cumulative petrol is less than the cumulative distance, update the starting point and reset the cumulative sums.
    -   Return the starting point if the total petrol is sufficient to cover the total distance.

### Code (C++)

```cpp
class Solution {
public:
    int tour(petrolPump p[], int n) {
        int totalPetrol = 0;
        int totalDistance = 0;
        int currentPetrol = 0;
        int startIndex = 0;
        
        for (int i = 0; i < n; ++i) {
            totalPetrol += p[i].petrol;
            totalDistance += p[i].distance;
            currentPetrol += p[i].petrol - p[i].distance;
            
            // If currentPetrol is less than 0, we cannot start from startIndex
            if (currentPetrol < 0) {
                // Update the startIndex to the next petrol pump
                startIndex = i + 1;
                // Reset currentPetrol for the new start index
                currentPetrol = 0;
            }
        }
        
        // If totalPetrol is less than totalDistance, it means the tour is not possible
        return (totalPetrol >= totalDistance) ? startIndex : -1;
    }
};

```

### Time Complexity:
- **O(n):** Each petrol pump is processed once

### Space Complexity:
- **O(1):** no extra space is used.

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>