# [Alien Dictionary](https://www.geeksforgeeks.org/problems/alien-dictionary/1)

![](https://badgen.net/badge/Level/Hard/red)

Given a sorted dictionary of an alien language having N words and k starting alphabets of standard dictionary. Find the order of characters in the alien language.
Note: Many orders may be possible for a particular test case, thus you may return any valid order and output will be 1 if the order of string returned by the function is correct else 0 denoting incorrect string returned.

### Approach Used :

-   Graph Representation:
    -   Treat each character in the alien language as a node in a directed graph.
    -   Construct the graph by comparing adjacent words in the dictionary. For each pair of adjacent words, find the first character that differs and create a directed edge from the character in the first word to the character in the second word.
-   Topological Sorting:
    -   After building the graph, apply Kahn's algorithm (BFS-based topological sort) to determine the order of characters.
    -   Characters with zero incoming edges (indegree) are added to the result, and their connected nodes' indegree is decreased. If a node's indegree becomes zero, it is added to the queue.

### Code (C++)

```cpp
class Solution {
public:
    string findOrder(string dict[], int N, int K) {
        vector<int> adj[K];
        vector<int> indegree(K, 0);
        string result = "";

        // Build the adjacency list
        for (int i = 0; i < N - 1; ++i) {
            string word1 = dict[i];
            string word2 = dict[i + 1];
            int len = min(word1.length(), word2.length());
            for (int j = 0; j < len; ++j) {
                if (word1[j] != word2[j]) {
                    adj[word1[j] - 'a'].push_back(word2[j] - 'a');
                    indegree[word2[j] - 'a']++;
                    break;
                }
            }
        }

        // Topological Sort (Kahn's Algorithm)
        queue<int> q;
        for (int i = 0; i < K; ++i) {
            if (indegree[i] == 0)
                q.push(i);
        }

        while (!q.empty()) {
            int u = q.front();
            q.pop();
            result += (u + 'a');
            for (int v : adj[u]) {
                if (--indegree[v] == 0)
                    q.push(v);
            }
        }

        return result;
    }
};

```

### Time Complexity:
- **O(n * l + k):** where N is the number of words, L is the average length of the words, and K is the number of unique characters (nodes in the graph). The time complexity arises from graph construction and topological sorting.

### Space Complexity:
- **O(k):** for storing the adjacency list, indegree array, and the result.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>