# [12. Integer to Roman](https://leetcode.com/problems/integer-to-roman/)

![](https://badgen.net/badge/Level/Medium/yellow)

Given an integer, convert it to a Roman numeral.
1 <= num <= 3999
### Approach Used :

-   To convert an integer to a Roman numeral, you can use a map of integer values to their corresponding Roman numeral symbols and process the number from the largest to the smallest value.

### Code (C++)

```cpp
class Solution {
public:
    string intToRoman(int num) {
        // Define mappings of integer values to Roman numerals
        vector<pair<int, string>> valueSymbols = {
            {1000, "M"}, {900, "CM"}, {500, "D"}, {400, "CD"},
            {100, "C"}, {90, "XC"}, {50, "L"}, {40, "XL"},
            {10, "X"}, {9, "IX"}, {5, "V"}, {4, "IV"}, {1, "I"}
        };
        
        string result;
        
        for (const auto& [value, symbol] : valueSymbols) {
            while (num >= value) {
                result += symbol;
                num -= value;
            }
        }
        
        return result;
    }
};
```

### Time Complexity:
- **O(n):** where n is interger num.

### Space Complexity:
- **O(1):** no extra space is used.


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>