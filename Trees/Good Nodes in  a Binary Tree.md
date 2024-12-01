
# Count Good Nodes in Binary Tree

Medium

Within a binary tree, a node `x` is considered **good** if the path from the root of the tree to the node `x` contains no nodes with a value greater than the value of node `x`

Given the root of a binary tree `root`, return the number of **good** nodes within the tree.

**Example 1:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/9bf374f1-71fe-469e-2840-5d223d9d1b00/public)

```java
Input: root = [2,1,1,3,null,1,5]

Output: 3
```

Copy

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/8df65da7-abac-4948-9a92-0bc7a8dda100/public)

**Example 2:**

```java
Input: root = [1,2,-1,3,4]

Output: 4
```

Copy

**Constraints:**

- `1 <= number of nodes in the tree <= 100`
- `-100 <= Node.val <= 100`


---

![[Trees/Tree.excalidraw.md#^group=Zl5Q990b|100%]]

### DFS

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
    int c = 0;

    void finder(TreeNode* root, int l) {
        if (root == nullptr) return ; // return value is dummy
        if(root->val >= l) c++;
        l = max(l, root->val);
        finder(root->left, l);
        finder(root->right, l);

    }
    int goodNodes(TreeNode* root) {
        finder(root, INT_MIN);
        return c;
    }
};
```

> Note: My runtime was higher than others' in this problem. I'll look at other approaches and ways for optimization when I visit this question again

