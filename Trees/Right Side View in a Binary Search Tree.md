# Binary Tree Right Side View

Solved 

Medium

You are given the `root` of a binary tree. Return only the values of the nodes that are visible from the right side of the tree, ordered from top to bottom.

**Example 1:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/d348893a-8917-456c-9599-c405cfc4e000/public)

```java
Input: root = [1,2,3]

Output: [1,3]
```

Copy

**Example 2:**

```java
Input: root = [1,2,3,4,5,6,7]

Output: [1,3,7]
```

Copy

**Constraints:**

- `0 <= number of nodes in the tree <= 100`
- `-100 <= Node.val <= 100`


---
![[Trees/Tree.excalidraw.md#^group=lhWU4nq3aQWUR2rP9RmCU|100%]]

![[Pasted image 20241130223945.png]]

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
    vector<int> vec;
    set<int> myset;
    vector<int> rightSideView(TreeNode* root,int depth=0) {
        if(root == nullptr) return vec;
        depth++;
        if(myset.find(depth) == myset.end()){
            vec.push_back(root->val);
            myset.insert(depth);
        }
        rightSideView(root->right,depth);
        rightSideView(root->left,depth);
        return vec;
    }
};

```

