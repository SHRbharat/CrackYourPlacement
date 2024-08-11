# [Phone directory](https://www.geeksforgeeks.org/problems/phone-directory4628/1)

![](https://badgen.net/badge/Level/Hard/red)

Given a list of contacts contact[] of length n where each contact is a string which exist in a phone directory and a query string s. The task is to implement a search query for the phone directory. Run a search query for each prefix p of the query string s (i.e. from  index 1 to |s|) that prints all the distinct contacts which have the same prefix as p in lexicographical increasing order. Please refer the explanation part for better understanding.
Note: If there is no match between query and contacts, print "0".

### Approach Used :

-   Trie Construction:
    -   Node Structure: Each Node in the Trie contains an array of links for each character of the alphabet, a boolean flag to mark the end of a word, and methods to interact with these components.
    -   Insertion: The insert method adds each contact to the Trie by iterating through its characters and creating new nodes as needed.
-   Prefix Search and Contact Display:
    -   Prefix Traversal: The displayContacts method traverses the Trie for each prefix of the query string s. It collects all contacts matching the current prefix using the printAll method.
    -   Contact Retrieval: The printAll method performs a depth-first search (DFS) from the current node to retrieve all words that are stored in the Trie and match the prefix.
-   Output Handling:
    -   For each prefix, if no contacts are found, add "0" to the results.
    -   Ensure that the result list contains outputs for all prefixes of the query string, filling with "0" if necessary.

### Code (C++)

```cpp
struct Node{
    Node* links[26];
    bool flag ;
    
    bool containsKey(char ch){
        return links[ch-'a']!=NULL;
    }
    
    void put(char ch){
        Node* node = new Node();
        links[ch-'a']= node;
    }
    
    Node* get(char ch)
   { return links[ch-'a'];}
    
    void setEnd()
    {flag = true;}
    
    
    bool getEnd(){
        return flag;
    }
    
};
  
class Solution{
public:
    Node*node;
    void insert(string word ,Node* root){
        Node*node = root;
        
        for(int i=0;i<word.size();i++){
            if(!node->containsKey(word[i])){
                node->put(word[i]);
                
            }
            
            node = node->get(word[i]);
        }
        
        node->setEnd();
       
    }
    
    void printAll(string str , vector<string>&temp , Node* node ){
         
        if(node->getEnd())
        temp.push_back(str);
        
       
        for(int i=0;i<26;i++){
            if(node->containsKey(i+'a')){
                
                str+=(i+'a');
                printAll(str , temp , node->get(i+'a'));
                str.pop_back();
            }
        }
       
    }
    

    vector<vector<string>> displayContacts(int n, string contact[], string s)
    {
        vector<vector<string>>ans;
        
       Node* root = new Node();
       for(int i=0;i<n;i++){
           insert(contact[i] , root);
       }
        
        node = root;
        string str = "";
        for(int i=0;i<s.length();i++){
       
            
            if(!node->containsKey(s[i])){
                ans.push_back({"0"});
                break;
            }
            
            else{
                vector<string>temp;
                node = node->get(s[i]);
                str+=s[i];
                printAll(str , temp ,node);
               
                ans.push_back(temp);
                
            }
        }
        
        
        while(ans.size()<s.length()){
            ans.push_back({"0"});
        }
        
        return ans;
    }
};
```

### Time Complexity:
- **O(n * m + s * (p + n * m)):**  where n is the number of contacts, m is the maximum length of a contact, and s is the length of the query string.

### Space Complexity:
- **O(n * m):** which includes the space for the Trie and the results.

### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>