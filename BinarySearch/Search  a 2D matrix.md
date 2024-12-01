[74. Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/)

Solved

Medium

Topics

Companies

You are given an `m x n` integer matrix `matrix` with the following two properties:

- Each row is sorted in non-decreasing order.
- The first integer of each row is greater than the last integer of the previous row.

Given an integer `target`, return `true` _if_ `target` _is in_ `matrix` _or_ `false` _otherwise_.

You must write a solution in `O(log(m * n))` time complexity.

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/10/05/mat.jpg)

**Input:** matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 3
**Output:** true

**Example 2:**

![](https://assets.leetcode.com/uploads/2020/10/05/mat2.jpg)

**Input:** matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]], target = 13
**Output:** false

**Constraints:**

- `m == matrix.length`
- `n == matrix[i].length`
- `1 <= m, n <= 100`
- `-104 <= matrix[i][j], target <= 104`

---

![[BinarySearch/BinarySearch.excalidraw.md#^group=5CuwJZ189yAHfY6UiaEO2|100%]]

```cpp
class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
        int top = 0;
        int bottom = matrix.size()-1;
        int n = matrix[0].size()-1;
        int cmid;
        int l,r,rmid;
        // find the correct row
        while(top <= bottom) {
            cmid = top + (bottom - top)/2;
            
            if(target == matrix[cmid][0]){return true;}

            if(target > matrix[cmid][0]) {
                l = 0;
                r = n;
                // search for rows here
                while(l<=r) {
                    rmid = l + (r-l)/2;

                    if (matrix[cmid][rmid] == target) {
                        return true;
                    }
                    if(target > matrix[cmid][rmid]) {
                        l = rmid+1;
                    }else{
                        r = rmid-1;
                    }
                    
                }
                top = cmid+1;
            }else{
                bottom = cmid-1;
            }
        }
        return false;
    }
};

```

[[Binary Search]]