# [Boyer Moore Algorithm for Pattern Searching](https://www.geeksforgeeks.org/boyer-moore-algorithm-for-pattern-searching/)

![](https://badgen.net/badge/Level/Hard/red)

Pattern searching is an important problem in computer science. When we do search for a string in a notepad/word file, browser, or database, pattern searching algorithms are used to show the search results.

A typical problem statement would be- 

” Given a text txt[0..n-1] and a pattern pat[0..m-1] where n is the length of the text and m is the length of the pattern, write a function search(char pat[], char txt[]) that prints all occurrences of pat[] in txt[]. You may assume that n > m. “

### Approach Used :

-   Bad Character Heuristic
The idea of bad character heuristic is simple. The character of the text which doesn’t match with the current character of the pattern is called the Bad Character. Upon mismatch, we shift the pattern until
    -   The mismatch becomes a match.
    -   Pattern P moves past the mismatched character.


### Code (C++)

```cpp
/* C++ Program for Bad Character Heuristic of Boyer
Moore String Matching Algorithm */
#include <bits/stdc++.h>
using namespace std;
#define NO_OF_CHARS 256
 
// The preprocessing function for Boyer Moore's
// bad character heuristic
void badCharHeuristic(string str, int size,
                      int badchar[NO_OF_CHARS])
{
    int i;
 
    // Initialize all occurrences as -1
    for (i = 0; i < NO_OF_CHARS; i++)
        badchar[i] = -1;
 
    // Fill the actual value of last occurrence
    // of a character
    for (i = 0; i < size; i++)
        badchar[(int)str[i]] = i;
}
 
/* A pattern searching function that uses Bad
Character Heuristic of Boyer Moore Algorithm */
void search(string txt, string pat)
{
    int m = pat.size();
    int n = txt.size();
 
    int badchar[NO_OF_CHARS];
 
    /* Fill the bad character array by calling
    the preprocessing function badCharHeuristic()
    for given pattern */
    badCharHeuristic(pat, m, badchar);
 
    int s = 0; // s is shift of the pattern with
               // respect to text
    while (s <= (n - m)) {
        int j = m - 1;
 
        /* Keep reducing index j of pattern while
        characters of pattern and text are
        matching at this shift s */
        while (j >= 0 && pat[j] == txt[s + j])
            j--;
 
        /* If the pattern is present at current
        shift, then index j will become -1 after
        the above loop */
        if (j < 0) {
            cout << "pattern occurs at shift = " << s
                 << endl;
 
            /* Shift the pattern so that the next
            character in text aligns with the last
            occurrence of it in pattern.
            The condition s+m < n is necessary for
            the case when pattern occurs at the end
            of text */
            s += (s + m < n) ? m - badchar[txt[s + m]] : 1;
        }
 
        else
            /* Shift the pattern so that the bad character
            in text aligns with the last occurrence of
            it in pattern. The max function is used to
            make sure that we get a positive shift.
            We may get a negative shift if the last
            occurrence of bad character in pattern
            is on the right side of the current
            character. */
            s += max(1, j - badchar[txt[s + j]]);
    }
}
 
/* Driver code */
int main()
{
    string txt = "ABAAABCD";
    string pat = "ABC";
    search(txt, pat);
    return 0;
}
```

### Time Complexity:
- **O(m * n):** The Bad Character Heuristic may take O(m*n) time in worst case. The worst case occurs when all characters of the text and pattern are same. For example, txt[] = “AAAAAAAAAAAAAAAAAA” and pat[] = “AAAAA”. The Bad Character Heuristic may take O(n/m) in the best case. The best case occurs when all the characters of the text and pattern are different. 

### Space Complexity:
- **O(1):** no extra space is used.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>