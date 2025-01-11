![[Trees/Tree.excalidraw.md#^group=Kr5dM7gY0y4irAGQS4D4K|100%]]



```cpp
#include <iostream>  
#include <queue>  
#include <vector>  
using namespace std;  
  
// Definition for a binary tree node.  
struct TreeNode {  
    int val;  
    TreeNode* left;  
    TreeNode* right;  
  
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}  
};  
  
class BinaryTree {  
public:  
    TreeNode* root;  
  
    BinaryTree() : root(nullptr) {}  
  
    // Insert nodes in level-order (Breadth-First manner).  
    void insertLevelOrder(const vector<int>& values) {  
        if (values.empty()) return;  
  
        root = new TreeNode(values[0]);  
        queue<TreeNode*> q;  
        q.push(root);  
  
        size_t i = 1;  
        while (!q.empty() && i < values.size()) {  
            TreeNode* node = q.front();  
            q.pop();  
  
            if (values[i] != -1) { // -1 represents NULL  
                node->left = new TreeNode(values[i]);  
                q.push(node->left);  
            }  
            i++;  
  
            if (i < values.size() && values[i] != -1) {  
                node->right = new TreeNode(values[i]);  
                q.push(node->right);  
            }  
            i++;  
        }  
    }  
  
    void play(TreeNode* root) {  
	  // leetcode workarea
    }  
};  
  
int main() {  
    BinaryTree tree;  
  
    // Example input to create the tree in level-order.  
    vector<int> values = {1, 2, 3, 4, 5, -1, 6, -1, -1, 7, 8, -1, -1, 9, 10}; // -1 represents NULL  
  
    // Build the binary tree.    tree.insertLevelOrder(values);  
  
    // Call the play() method with the root node.  
    tree.play(tree.root);  
  
    return 0;  
}  
  
```

```
                1
             /     \
           2         3
         /   \        \
       4      5        6
             /  \
            7    8
                 / \
                9   10

```

### DFS

#### PreOrder Traversal : DFS

```cpp
void dfs(TreeNode *root) {  
    if (!root) return;  
    cout << root->val << "\t";  
    dfs(root->left);  
    dfs(root->right);  
}
```

#### Inorder Traversal : DFS

```cpp
void dfs(TreeNode *root) {  
    if (!root) return;  
    dfs(root->left);  
    cout << root->val << "\t";  
    dfs(root->right);  
}
```

#### PostOrder Traversal : DFS

```cpp
void dfs(TreeNode *root) {  
    if (!root) return;  
    dfs(root->left);  
    dfs(root->right);  
    cout << root->val << "\t";  
}
```


### Print all the Leaf Nodes in  a Binary Tree
*Crafted by me*

```cpp
void dfs(TreeNode *root) {  
    if (!root)  return;  
  
    if (!root->left && !root->right) {  
        // this is true in case of leaf node  
        cout << "LeafNode " << root->val << endl;  
    }  
  
    dfs(root->left);  
    dfs(root->right);  
  
}
```

### MaxHeight of a Binary Tree




## Breadth First Search(BFS) :  

```cpp
// written by own.. worked for simple case.. yet to verify this
void bfs(TreeNode* root) {  
    if (!root) return;  
    queue<TreeNode*> Q;  
    Q.push(root);  
    TreeNode *cur;  
    while (!Q.empty()) {  
        cur = Q.front();  
        cout << cur->val << '\t';  
  
        if (cur->left) {  
            Q.push(cur->left);  
        }  
  
        if (cur->right) {  
            Q.push(cur->right);  
        }  
        Q.pop();  
    }  
}
```

