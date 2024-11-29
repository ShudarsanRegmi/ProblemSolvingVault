# Subtree of Another Tree

Easy

Given the roots of two binary trees `root` and `subRoot`, return `true` if there is a subtree of `root` with the same structure and node values of `subRoot` and `false` otherwise.

A subtree of a binary tree `tree` is a tree that consists of a node in `tree` and all of this node's descendants. The tree `tree` could also be considered as a subtree of itself.

**Example 1:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/2991a77a-9664-46ed-528d-019e392f7400/public)

```java
Input: root = [1,2,3,4,5], subRoot = [2,4,5]

Output: true
```

Copy

**Example 2:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/ae6114cb-23a0-457f-c441-0a82b7a58500/public)

```java
Input: root = [1,2,3,4,5,null,null,6], subRoot = [2,4,5]

Output: false
```

Copy

**Constraints:**

- `0 <= The number of nodes in both trees <= 100`.
- `-100 <= root.val, subRoot.val <= 100`

---
![[Trees/Tree.excalidraw.md#^group=teVOWnxE|100%]]

## Pseudo Code

```
algo:
for each node in main tree do dfs with subtree


dfsMain(node *root)
if(node == nullptr) return 0;

dfsMain(root->left);
if (childDfs(root, subroot)) return 1;
dfsMain(root->right);

return false;



childdfs(node, subroot)

childdfs(node* p, node*c):
if(p == nullptr && c == nullptr) return true;

if (p == nullptr || c == nulptr) return false;

if(p->val == q->val):
    return childdfs(p->left, q->left) && childdfs(p->right, q->right);

return false;
```

### Code Implementation 
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

    bool childDFS(TreeNode* p, TreeNode* c){
        if(p == nullptr && c == nullptr) return true;
        if(p== nullptr || c == nullptr) return false;

        if(p->val == c->val) {
	        return childDFS(p->left, c->left) && childDFS(p->right, c->right);
        }
        return false;
    }
    
    int mainDFS(TreeNode *root,TreeNode *subRoot) {
        if(root == nullptr) return 0;


        int l = mainDFS(root->left,subRoot);
        if (childDFS(root, subRoot)) return 1;
        int r = mainDFS(root->right,subRoot);

        if (l == 1 || r== 1) return 1;
        return 0;
    }

    bool isSubtree(TreeNode* root, TreeNode* subRoot) {
        if (mainDFS(root, subRoot) == 1) {
            return true;
        }else{
            return false;
        }

    }
};

```

