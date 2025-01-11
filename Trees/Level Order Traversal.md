
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


### Crafted by own

```cpp
vector<vector<int>> bfs(TreeNode* root) {  
    if (!root) return{};  
    queue<TreeNode*> Q;  
    Q.push(root);  
    TreeNode *cur;  
    vector<vector<int>> vecs;  
    while (!Q.empty()) {  
        int size = Q.size();  
        vector<int> vec;  
  
        for (int i=0; i<size; i++) {  
            cur = Q.front();  
            cout << cur->val << '\t';  
  
            if (cur->left) {  
                Q.push(cur->left);  
                vec.push_back(cur->left->val);  
            }  
  
            if (cur->right) {  
                Q.push(cur->right);  
                vec.push_back(cur->right->val);  
            }  
            Q.pop();  
        }  
        vecs.push_back(vec);  
    }
```

> In this code, I'm pushing child in my level vectors... so I'm not being able to encapsulate the logic of root node within the  loop.. 

## Fixed Logic

```cpp
vector<vector<int>> bfs(TreeNode* root) {  
    if (!root) return{};  
    queue<TreeNode*> Q;  
    Q.push(root);  
    TreeNode *cur;  
    vector<vector<int>> vecs;  
    while (!Q.empty()) {  
        int size = Q.size();  
        vector<int> vec;  
  
        for (int i=0; i<size; i++) {  
            cur = Q.front();  
            cout << cur->val << '\t';  
            vec.push_back(cur->val);  
            if (cur->left) {  
                Q.push(cur->left);  
            }  
  
            if (cur->right) {  
                Q.push(cur->right);  
            }  
            Q.pop();  
        }  
        vecs.push_back(vec);  
    }  
  
    return vecs;  
}
```

