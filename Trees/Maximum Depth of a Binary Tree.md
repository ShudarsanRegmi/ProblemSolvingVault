
[104. Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

Attempted

Easy

Topics

Companies

Given the `root` of a binary tree, return _its maximum depth_.

A binary tree's **maximum depth** is the number of nodes along the longest path from the root node down to the farthest leaf node.

**Example 1:**

![](https://assets.leetcode.com/uploads/2020/11/26/tmp-tree.jpg)

**Input:** root = [3,9,20,null,null,15,7]
**Output:** 3

**Example 2:**

**Input:** root = [1,null,2]
**Output:** 2

**Constraints:**

- The number of nodes in the tree is in the range `[0, 104]`.
- `-100 <= Node.val <= 100`
---

![[Trees/Tree.excalidraw.md#^group=55VIZ5XV9b3bTIOheZh0Q|100%]]

## Brute Force Approach

```
dfs(root,depth)
	depth++
	depths.append(depth);
	dfs(root->left)
	dfs(root->right);

return max(depths)
```

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
    vector<int> depths;
    void maxxDepth(TreeNode *root,int depth){
        if(root != nullptr) { 
            depth++;
            depths.push_back(depth);
            maxxDepth(root->left, depth);
            maxxDepth(root->right, depth);
        }
        
    }
    int maxDepth(TreeNode* root) {
        if(root == nullptr) {return 0;}
        maxxDepth(root,0);
        return *max_element(depths.begin(), depths.end());
    }
};
```


### DFS

![[Trees/Tree.excalidraw.md#^group=VDwfuTzs|100%]]



```cpp
int maxDepth(TreeNode* root) {
	if (!root) return 0;
	int left = maxDepth(root->left);
	int right = maxDepth(root->right);

	return 1 + max(left, right);
}
```

