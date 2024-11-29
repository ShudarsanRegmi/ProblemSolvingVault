
![[Trees/Tree.excalidraw.md#^group=ua68n54m|100%]]


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

    int Height(TreeNode* root) {
        if(!root) return 0;

        int leftHeight = Height(root->left);
        int rightHeight = Height(root->right);

        if (leftHeight == -1 || 
	        rightHeight == -1 ||
	        abs(leftHeight-rightHeight) > 1) return -1;
        
        return 1 + max(leftHeight, rightHeight);


    }
    
    bool isBalanced(TreeNode* root) {
        if (Height(root) == -1) {
            return false;
        }
        return true;
    }
};

```

### Importance of `leftHeight == -1 || rightHeight == -1`

This ensures that if a subtree is already unbalanced at any level, the imbalance is propagated up the tree without further calculations.

<p style='color:red; font-size:20px'>I've written this by looking at solution</p>
<p style='color:green; font-size:20px'>I'll try to solve it again by myself</p>
