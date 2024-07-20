# [67. Add Binary](https://leetcode.com/problems/add-binary/)

![](https://badgen.net/badge/Level/Easy/green)

Given two binary strings a and b, return their sum as a binary string.

### Approach Used :

-   The solution performs binary addition by iterating through the strings from right to left, adding corresponding digits and managing the carry. The result is built as a string in reverse order, which is then reversed at the end to obtain the final binary sum.

### Code (C++)

```cpp
class Solution {
 public:
  string addBinary(string a, string b) {
    string ans;
    int carry = 0;
    int i = a.length() - 1;
    int j = b.length() - 1;

    while (i >= 0 || j >= 0 || carry) {
      if (i >= 0)
        carry += a[i--] - '0';
      if (j >= 0)
        carry += b[j--] - '0';
      ans += carry % 2 + '0';
      carry /= 2;
    }

    reverse(ans.begin(), ans.end());
    return ans;
  }
};
```

### Time Complexity:
- **O(max(n,m)):** itrates equal to length of longer string

### Space Complexity:
- **O(max(n,m)):** creates a resultant string


### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>