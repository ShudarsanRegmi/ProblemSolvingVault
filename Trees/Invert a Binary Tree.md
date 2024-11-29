![[Trees/Tree.excalidraw.md#^group=H1O4U23rW3DbtZAiK_f2E|100%]]

### Algorithm

```
node* dfs(node *root):
	if root==nullptr return nullptr
	Node *Node = new Node(root->val)
	node->right = dfs(root->left)
	node->left = dfs(root->right)
	return node
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
    TreeNode* invertTree(TreeNode* root) {
        if(root == nullptr) return nullptr;

        TreeNode* node = new TreeNode(root->val);
        node->right = invertTree(root->left);
        node->left = invertTree(root->right);

        return node;
    }
};

```
