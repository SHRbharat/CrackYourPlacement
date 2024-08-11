# [Word Break (Trie)](https://www.geeksforgeeks.org/problems/word-break-trie--141631/1)

![](https://badgen.net/badge/Level/Hard/red)

Given a string A and a dictionary of n words B, find out if A can be segmented into a space-separated sequence of dictionary words. 

### Approach Used :

-   Trie Construction:
    -   The insert method constructs the Trie by adding each word from the dictionary.
-   Dynamic Programming with Trie:
    -   dp[i] is true if the substring A[0..i-1] can be segmented into dictionary words.
    -   Traverse through the string A, and for each valid starting position i, use the Trie to check all possible endings of valid words from that position. Update dp[j + 1] to true if a valid word ending is found.
-   Dynamic Programming Array:
    -   Initialize dp[0] to true because an empty string is trivially segmented.
    -   Use the canSegment method to fill the dp array based on the Trie.

### Code (C++)

```cpp
class Node{
    public:
    Node* children[26];
    bool isTerminal;
    Node()
    {
        for(int i=0;i<26;i++){
          this->children[i]=NULL;
        }
        
        this->isTerminal = false;
    }
};

class Trie{
    private:
    Node* root;
    public:
    Trie()
    {
        root=new Node();
    }
    
    void insert(string &str)
    {
        Node* curr = root;
        for(int i=0;i<str.size();i++)
        {
            int index = str[i]-'a';
            if(curr->children[index]==NULL)
            {
                curr->children[index] = new Node();
            }
            curr=curr->children[index];
        }
        curr->isTerminal = true;
    }
    
    bool solve(string str,int start)
    {
        if(start>=str.size())
        return true;
        Node* curr = root;
        bool ans = 0;
        for(int i=start;i<str.size();i++)
        {
            int index = str[i]-'a';
            if(curr->children[index]==NULL)
            return false;
            else{
                 curr=curr->children[index];
                 if(curr->isTerminal==true)
                 {
                   if(solve(str,i+1)==true)
                   return true;
                 }
            }
        }
        return false;
    }
    
};

class Solution{
    public:
    // A : given string to search
    // B : vector of available strings
    
    int wordBreak(string A, vector<string> &B) {
        //code here
        Trie trie;
        for(int i=0;i<B.size();i++)
        {
            trie.insert(B[i]);
        }
        
        return trie.solve(A,0);
    }
};
```

### Time Complexity:
- **O(n<sup>2</sup> * m):** where n is the length of the string A and m is the average length of dictionary words. The complexity arises from traversing the string and checking prefixes using the Trie.

### Space Complexity:
- **O(n * m):** for storing the Trie and the DP array.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>