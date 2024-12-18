

[1768. Merge Strings Alternately](https://leetcode.com/problems/merge-strings-alternately/)

Solved

Easy

Topics

Companies

Hint

You are given two strings `word1` and `word2`. Merge the strings by adding letters in alternating order, starting with `word1`. If a string is longer than the other, append the additional letters onto the end of the merged string.

Return _the merged string._

**Example 1:**

**Input:** word1 = "abc", word2 = "pqr"
**Output:** "apbqcr"
**Explanation:** The merged string will be merged as so:
word1:  a   b   c
word2:    p   q   r
merged: a p b q c r

**Example 2:**

**Input:** word1 = "ab", word2 = "pqrs"
**Output:** "apbqrs"
**Explanation:** Notice that as word2 is longer, "rs" is appended to the end.
word1:  a   b 
word2:    p   q   r   s
merged: a p b q   r   s

**Example 3:**

**Input:** word1 = "abcd", word2 = "pq"
**Output:** "apbqcd"
**Explanation:** Notice that as word1 is longer, "cd" is appended to the end.
word1:  a   b   c   d
word2:    p   q 
merged: a p b q c   d

**Constraints:**

- `1 <= word1.length, word2.length <= 100`
- `word1` and `word2` consist of lowercase English letters.


---
## My Solution

```cpp
class Solution {
public:
    string mergeAlternately(string word1, string word2) {
        string finalstr;
        int x = 0;
        int p1 = 0, p2 = 0;

        while (p1 != word1.size() && p2 != word2.size()) {
            if(x % 2 == 0) {
                finalstr += word1[p1];
                p1++;
            }else{
                finalstr += word2[p2];
                p2++;
            }
            x++;
        }

        if (p1 == word1.size()) {
            while (p2 < word2.size()) {
                finalstr += word2[p2];
                p2++;
            }
        }

        if (p2 == word2.size()) {
            while (p1 < word1.size()) {
                finalstr += word1[p1];
                p1++;
            }
        }

        return finalstr;
    }
};

```

## Smart Solution

```cpp
class Solution {
public:
    string mergeAlternately(string word1, string word2) {
        std::string merged;
        int maxLength = std::max(word1.length(), word2.length());

        for (int i = 0; i < maxLength; i++) {
            if (i < word1.length()) {
                merged += word1[i];
            }
            
            if (i < word2.length()) {
                merged += word2[i];
            }
        }

        return merged;        
    }
};

```

#algomap
#easy 