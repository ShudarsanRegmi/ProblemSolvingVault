
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
    queue<TreeNode*> Q;
    vector<vector<int>> vec;

    vector<vector<int>> levelOrder(TreeNode* root) {
        if (root == nullptr) return {};
        Q.push(root);
        int size;
        while (!Q.empty()){
            vector<int> levelVec;
            size = Q.size();

           
           
            for(int i=0; i<size; i++){
                levelVec.push_back(Q.front()->val);
                 if(Q.front()->left != nullptr) {
                    Q.push(Q.front()->left);
                }
                if(Q.front()->right != nullptr) {
                    Q.push(Q.front()->right);
                }
                Q.pop();
            }

            vec.push_back(levelVec);
        }
        return vec;
    }
};


```