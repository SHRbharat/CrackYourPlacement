# [Print all the duplicate characters in a string](https://www.geeksforgeeks.org/print-all-the-duplicates-in-the-input-string/)

![](https://badgen.net/badge/Level/Easy/green)

Given a string S, the task is to print all the duplicate characters with their occurrences in the given string.

### Approach Used-1 (sorting):

-   If we sort the string then all duplicates will come together in the string. Then, traverse the string from starting index to the ending index and check if the neighbor character is same then increment the count by 1.

### Code-1 (C++)

```cpp
void printDuplicates(string str)
{
    int len = str.length();

    // Sorting the string
    sort(str.begin(), str.end());

    // Loop through the sorted string to find duplicates
    for (int i = 0; i < len; i++) {
        int count = 1;

        // Counting the occurrences of each character
        while (i < len - 1 && str[i] == str[i + 1]) {
            count++;
            i++;
        }

        // Printing the duplicate character and its count
        if (count > 1) {
            cout << str[i] << ", count = " << count << endl;
        }
    }
}
```

### Time Complexity:
- **O(nlogn):** due to sorting

### Space Complexity:
- **O(n):** if frequency is stored.

### Approach Used-2 (hashing):

-   Store the characters count of a string in an unordered map which allows operations in constant time.Then, print the characters which have a frequency greater than 1.

### Code-2 (C++)

```cpp
void printDups(string str)
{
    unordered_map<char, int> count;
    for (int i = 0; i < str.length(); i++) {
        count[str[i]]++;
    }
    // iterating through the unordered map
    for (auto it : count) {
        if (it.second > 1)
            cout << it.first << ", count = " << it.second
                 << "\n";
    }
}
```

### Time Complexity:
- **O(n):** traverses the array once

### Space Complexity:
- **O(n):** space used for storing frequencies.
### Connect With Me : 

<a href="https://www.linkedin.com/in/shivam-ray-b4306524a/" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"></a>
<a href="https://x.com/rai_shivam11/" target="_blank"><img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" alt="X (formerly Twitter)">
</a>
<a href="https://leetcode.com/u/shrunited0702/" target="_blank"><img src="https://img.shields.io/badge/LeetCode-000000?style=for-the-badge&logo=LeetCode&logoColor=#d16c06" alt="leetcode">
</a>