[136. Single Number](https://leetcode.com/problems/single-number/)

Solved

Easy

Topics

Companies

Hint

Given a **non-empty** array of integers `nums`, every element appears _twice_ except for one. Find that single one.

You must implement a solution with a linear runtime complexity and use only constant extra space.

**Example 1:**

**Input:** nums = [2,2,1]
**Output:** 1

**Example 2:**

**Input:** nums = [4,1,2,1,2]
**Output:** 4

**Example 3:**

**Input:** nums = [1]
**Output:** 1

**Constraints:**

- `1 <= nums.length <= 3 * 104`
- `-3 * 104 <= nums[i] <= 3 * 104`
- Each element in the array appears twice except for one element which appears only once.

---
```cpp
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        // xor all the elementsi n the nums
        int xorsum = 0;
        for(int i : nums) {
            xorsum = xorsum ^ i;
        }
        return xorsum;
    }
};

```

>xor sum of two elements is 0 if they're same
