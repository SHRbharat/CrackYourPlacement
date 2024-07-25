# [168. Excel Sheet Column Title](https://leetcode.com/problems/excel-sheet-column-title/)

![](https://badgen.net/badge/Level/Easy/green)

Given an integer columnNumber, return its corresponding column title as it appears in an Excel sheet.

### Approach Used :

-   repeatedly map the remainder when divided by 26 to a character ('A'-'Z'), append it to the result string, and update columnNumber by dividing it by 26 until it becomes 0. Finally, reverse the result string to get the correct column title.

### Code (C++)

```cpp
class Solution {
public:
    string convertToTitle(int columnNumber) {
        string res;

        while (columnNumber > 0) {
            columnNumber--;  // Decrement columnNumber to make it 0-based
            int remainder = columnNumber % 26;
            res += (remainder + 'A');  
            columnNumber /= 26;
        }

        reverse(res.begin(), res.end());  // Reverse the result string
        return res;
    }
};

```

### Time Complexity:
- **O(log<sub>26</sub>n):** The number of iterations of the loop is proportional to the number of digits in the base-26 representation of columnNumber.

### Space Complexity:
- **O(1):** no extra space is used.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>