# Diameter of Binary Tree

Easy

The **diameter** of a binary tree is defined as the **length** of the longest path between _any two nodes within the tree_. The path does not necessarily have to pass through the root.

The **length** of a path between two nodes in a binary tree is the number of edges between the nodes.

Given the root of a binary tree `root`, return the **diameter** of the tree.

**Example 1:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/90e1d7a0-4322-4c5d-c59b-dde2bf92bb00/public)

```java
Input: root = [1,null,2,3,4,5]

Output: 3
```

Copy

Explanation: 3 is the length of the path `[1,2,3,5]` or `[5,3,2,4]`.

**Example 2:**

```java
Input: root = [1,2,3]

Output: 2
```

Copy

**Constraints:**

- `1 <= number of nodes in the tree <= 100`
- `-100 <= Node.val <= 100`
---

```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */

class Solution {
public:
    int res = 0;
    int dfs(TreeNode *root){
        if (!root) return 0;
        int left = dfs(root->left);
        int right = dfs(root->right);
        res = max(res, left+right);
        return 1 + max(left, right);
    }
    int diameterOfBinaryTree(TreeNode* root) {
        dfs(root);
        return res;
    }
};
```

<p style='color:red;font-size:20px'>I need to look at this again. I've written this by looking at a solution</p>

