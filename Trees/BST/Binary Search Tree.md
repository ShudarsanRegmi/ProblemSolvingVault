
```cpp
// Binary Search Tree operations in C++  
  
#include <iostream>  
using namespace std;  
  
struct node {  
    int key;  
    struct node *left, *right;  
};  
  
// Create a node  
struct node *newNode(int item) {  
    struct node *temp = (struct node *)malloc(sizeof(struct node));  
    temp->key = item;  
    temp->left = temp->right = NULL;  
    return temp;  
}  
  
// Inorder Traversal  
void inorder(struct node *root) {  
    if (root != NULL) {  
        // Traverse left  
        inorder(root->left);  
  
        // Traverse root  
        cout << root->key << " -> ";  
  
        // Traverse right  
        inorder(root->right);  
    }  
}  
  
  
struct node *insert(struct node *node, int key) {  
    if  (node == nullptr) {  
        // insert here...  
        return newNode(key);  
    }  
    if (key < node->key) {  
        node->left = insert(node->left, key);  
    }else {  
        node->right = insert(node->right, key);  
    }  
    return node; // I don't know why I always miss this line. I know I've less insights in this  
}  
  
// find the inorder successor  
struct node *minValueNode(struct node *node) {  
    // inorder successor is the smallest node of right subtree  
    struct node *current = node;  
  
    // find the leftmost leaf  
    while (current && current->left != nullptr)  
        current = current->left;  
    return current;  
}  
  
// write a function to delete a node in a binary serach tree  

  
  
// Driver code  
int main() {  
    struct node *root = NULL;  
    root = insert(root, 8);  
    root = insert(root, 3);  
    root = insert(root, 1);  
    root = insert(root, 6);  
    root = insert(root, 7);  
    root = insert(root, 10);  
    root = insert(root, 14);  
    root = insert(root, 4);  
  
    cout << "Inorder traversal: ";  
    inorder(root);  
  
    cout << "\nAfter deleting 10\n";  
    root = deleteNode(root, 10);  
    cout << "Inorder traversal: ";  
    inorder(root);  
}
```
<p style='color:red; font-size: 24px'> Delete function has wasted a lot of time </p>
