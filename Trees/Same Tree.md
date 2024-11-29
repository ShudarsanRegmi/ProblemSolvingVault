# Same Binary Tree

Solved 

Easy

Given the roots of two binary trees `p` and `q`, return `true` if the trees are **equivalent**, otherwise return `false`.

Two binary trees are considered **equivalent** if they share the exact same structure and the nodes have the same values.

**Example 1:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/e78fc10c-4692-471f-5261-61e9be4f3a00/public)

```java
Input: p = [1,2,3], q = [1,2,3]

Output: true
```

Copy

**Example 2:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/0b0ee764-c643-46ff-cb3f-86ce8b58ab00/public)

```java
Input: p = [4,7], q = [4,null,7]

Output: false
```

Copy

**Example 3:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/4d811f95-0488-490b-1f4f-fc5489df0f00/public)

```java
Input: p = [1,2,3], q = [1,3,2]

Output: false
```

Copy

**Constraints:**

- `0 <= The number of nodes in both trees <= 100`.
- `-100 <= Node.val <= 100`

---

![[Trees/Tree.excalidraw.md#^group=JkV1XqBYexdoNRZFhktBx|100%]]


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
    bool isSameTree(TreeNode* p, TreeNode* q) {
        if(p == nullptr && q == nullptr) return true;

        if(p==nullptr || q == nullptr) return false;

        if(p->val == q->val) {
            return isSameTree(p->left, q->left) && isSameTree(p->right, q->right);
        }else{
            return false;
        }
    }
};
```