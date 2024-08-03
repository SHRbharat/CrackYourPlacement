# [The Celebrity Problem](https://www.geeksforgeeks.org/problems/the-celebrity-problem/1)

![](https://badgen.net/badge/Level/Medium/yellow)

A celebrity is a person who is known to all but does not know anyone at a party. A party is being organized by some people.  A square matrix mat is used to represent people at the party such that if an element of row i and column j is set to 1 it means ith person knows jth person. You need to return the index of the celebrity in the party, if the celebrity does not exist, return -1.

### Approach Used-1 (stack) :

-   Push All Persons to Stack:
    -   Push all the indices (representing persons) onto a stack.
-   Identify a Potential Celebrity:
    -   Pop two persons from the stack and compare them:
        -   If person A knows person B, then A cannot be the celebrity, push B back to the stack.
        -   If person A does not know person B, then B cannot be the celebrity, push A back to the stack.
    -   Repeat this process until only one person remains in the stack. This person is the potential celebrity.
-   Validate the Potential Celebrity:
    -   Check if the remaining person in the stack is actually a celebrity by ensuring two conditions:
        -   The potential celebrity does not know anyone else.
        -   Everyone else knows the potential celebrity.

### Code-1 (C++)

```cpp
class Solution {
public:
    int celebrity(std::vector<std::vector<int>>& mat) {
        int n = mat.size();
        std::stack<int> s;

        // Step 1: Push all persons to the stack
        for (int i = 0; i < n; ++i) {
            s.push(i);
        }

        // Step 2: Find the potential celebrity
        while (s.size() > 1) {
            int a = s.top();
            s.pop();
            int b = s.top();
            s.pop();

            if (mat[a][b] == 1) {
                // a knows b, so a can't be a celebrity, but b might be
                s.push(b);
            } else {
                // a does not know b, so b can't be a celebrity, but a might be
                s.push(a);
            }
        }

        // The remaining person in the stack is the potential celebrity
        int candidate = s.top();

        // Step 3: Validate the candidate
        for (int i = 0; i < n; ++i) {
            if (i != candidate) {
                if (mat[candidate][i] == 1 || mat[i][candidate] == 0) {
                    return -1;
                }
            }
        }

        return candidate;
    }
};
```

### Time Complexity:
- **O(n):** The process of finding the potential celebrity involves popping and pushing elements from the stack which takes linear time.
The validation step also takes linear time as we need to check the conditions for each person.


### Space Complexity:
- **O(n):** due to stack.

### Approach Used-2 (two pointers) :

-   Initial Candidate Selection:
    -   Use two pointers technique to find a potential celebrity candidate.
    -   Start with two pointers, i and j, initialized to 0 and n-1 respectively (where n is the number of people at the party).
    -   Move the pointers towards each other based on the condition mat[i][j]:
        -   If mat[i][j] == 1, it means i knows j, so i cannot be a celebrity. Move i to i+1.
        -   If mat[i][j] == 0, it means i does not know j, so j cannot be a celebrity. Move j to j-1.
    -   The meeting point of i and j will give us a potential celebrity candidate.
-   Validation:
    -   Validate the candidate by checking two conditions:
        -   The candidate should not know anyone: mat[candidate][k] == 0 for all k from 0 to n-1 (except candidate itself).
        -   Everyone should know the candidate: mat[k][candidate] == 1 for all k from 0 to n-1 (except candidate itself).
-   Return Result:
    -   If the candidate passes both conditions, return the candidate's index.
    -   Otherwise, return -1 indicating there is no celebrity.

### Code-2 (C++)

```cpp
class Solution {
public:
    int celebrity(std::vector<std::vector<int>>& mat) {
        int n = mat.size();
        std::stack<int> s;

        // Step 1: Push all persons to the stack
        for (int i = 0; i < n; ++i) {
            s.push(i);
        }

        // Step 2: Find the potential celebrity
        while (s.size() > 1) {
            int a = s.top();
            s.pop();
            int b = s.top();
            s.pop();

            if (mat[a][b] == 1) {
                // a knows b, so a can't be a celebrity, but b might be
                s.push(b);
            } else {
                // a does not know b, so b can't be a celebrity, but a might be
                s.push(a);
            }
        }

        // The remaining person in the stack is the potential celebrity
        int candidate = s.top();

        // Step 3: Validate the candidate
        for (int i = 0; i < n; ++i) {
            if (i != candidate) {
                if (mat[candidate][i] == 1 || mat[i][candidate] == 0) {
                    return -1;
                }
            }
        }

        return candidate;
    }
};
```

### Time Complexity:
- **O(n):** The first loop runs in O(n) time to find the candidate.
The second loop also runs in O(n) time to validate the candidate.


### Space Complexity:
- **O(1):** no extra space is used.
### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>