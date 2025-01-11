![[LinkedList/LinkedList.excalidraw.md#^group=UJVMz2VUcYonJl4A57ogK|100%]]



### Print Linked List
```cpp
void printAlternately(Node* head) {  
    Node *temp = head;  
    while (temp) {  
        cout << temp->data << '\t';  
        temp = temp->next;  
    }  
}
```

### Print without processing the last node
```cpp
void printAlternately(Node* head) {  
    Node *temp = head;  
    while (temp->next) {  
        cout << temp->data << '\t';  
        temp = temp->next;  
    }  
}
```

### Print Alternatively

```cpp
void printAlternatively(Node* head) {
    Node* temp = head;
    while (temp) {
        cout << temp->data << '\t'; // Print current node
        if (temp->next == nullptr) break; // If next is null, stop
        temp = temp->next->next; // Move two steps ahead
    }
    cout << endl;
}
```

### Reverse a Linked List
```cpp
Node* reverse(Node* head) {  
    Node *temp = head;  
    Node *prev = nullptr;  
    Node *curr = head;  
    while (curr) {  
        temp = temp->next;  
        curr->next = prev; // this line disconnects to next node and connects toprevious node  
        prev = curr;  
        curr = temp;  
    }  
    return prev;  
  
}
```
### Delete the head node

```cpp
Node* deleteHead(Node* head) {  
    if (!head) return nullptr;  
  
        Node *prevHead;  
        prevHead = head;  
        head = head->next;  
        delete prevHead;  
        return head;  
}
// make sure to use the new head returned by deleteHead function
```

### Delete tail node
```cpp
Node* deleteTail(Node* head) {
    if (!head) {
        // Handle the empty list case
        return nullptr;
    }

    if (!head->next) {
        // Handle the single-node list case
        delete head;
        return nullptr;
    }

    Node* temp = head;

    // Traverse to the second-to-last node
    while (temp->next && temp->next->next) {
        temp = temp->next;
    }

    // Delete the tail node
    delete temp->next;
    temp->next = nullptr;

    return head;
}
```


### Getting the middle node using fast and slow pointer
```cpp
Node *fast = head, *slow = head;
while(fast && fast->next) {
	slow = slow->next;
	fast = fast->next->next;
}
```
<p style='color:green'> <li style='color:green'> slow points to the exact middle in case of odd no. of hodes</li>
<li style='color:green'> [middleLeft, middleRight] and <span style='color:pink'>middleRight </span>node in case of even of. of nodes i</p>
```cpp
Node *fast = head, *slow = head->next;
while(fast && fast->next) {
	slow = slow->next;
	fast = fast->next->next;
}
```

<p style='color:green'> <li style='color:green'> slow points to the exact middle in case of odd no. of hodes</li>
<li style='color:green'> [middleLeft, middleRight] and <span style='color:pink'>middleLeft </span> node in case of even of. of nodes i</p>

![[LinkedList/LinkedList.excalidraw.md#^group=Zlbt6kM5|100%]]

### Playing code

```cpp
#include <iostream>  
using namespace std;  
  
// Define a node structure  
struct Node {  
    int data;  
    Node* next;  
    Node(int val) : data(val), next(nullptr) {}  
};  
  
// Utility function to create a linked list from an array  
Node* createLinkedList(const int arr[], int size) {  
    if (size == 0) return nullptr;  
  
    Node* head = new Node(arr[0]);  
    Node* temp = head;  
  
    for (int i = 1; i < size; ++i) {  
        temp->next = new Node(arr[i]);  
        temp = temp->next;  
    }  
  
    return head;  
}  
  
// Utility function to display the linked list  
void printLinkedList(Node* head) {  
    while (head != nullptr) {  
        cout << head->data << " -> ";  
        head = head->next;  
    }  
    cout << "nullptr" << endl;  
}  
  
// Function to print nodes alternatively  
void printAlternately(Node* head) {  
    Node *temp = head;  
    while (temp->next) {  
        cout << temp->data << '\t';  
        temp = temp->next;  
        cout << "here..";  
    }  
}  
  
Node* reverse(Node* head) {  
    Node *temp = head;  
    Node *prev = nullptr;  
    Node *curr = head;  
    while (curr) {  
        temp = temp->next;  
        curr->next = prev;  
        prev = curr;  
        curr = temp;  
    }  
    return prev;  
}  
  
Node* deleteHead(Node* head) {  
    if (!head) return nullptr;  
  
        Node *prevHead;  
        prevHead = head;  
        head = head->next;  
        delete prevHead;  
        return head;  
}  
// Node *deleteTail(Node * head) {  
//     Node *temp;  
//     while (temp && temp->next && temp->next) {  
//         temp = temp->next;  
//     }  
//  
//     cout << temp->data << endl;  
// }  
  
Node *delteExactMiddle(Node *head) {  
    if (!head || !head->next) return nullptr; // empty list  
      
    // It works properly if the no. of nodes is more than two    Node *slow = head, *fast = head;  
    Node *prev = nullptr;  
    while (fast && fast->next) {  
        prev = slow;  
        slow=slow->next;  
        fast=fast->next->next;  
    }  
    prev->next = slow->next;  
    delete slow;  
    // slow points to the middle node  
    cout << slow->data;  
}  
  
Node* findSecondLastNode(Node* head) {  
    if (!head || !head->next) {  
        // Return nullptr if the list is empty or has only one node  
        return nullptr;  
    }  
  
    Node* temp = head;  
    while (temp->next && temp->next->next) {  
        // temp->next is not nullptr (we're not at the last node).  
        // temp->next->next is not nullptr (the next node is not the last node).        temp = temp->next;  
    }  
    return temp;  
}  
  
  
int main() {  
    int arr[] = {1, 2, 3, 4, 5, 6,7}; // Example array  
    int size = sizeof(arr) / sizeof(arr[0]);  
  
    // Create the linked list  
    Node* head = createLinkedList(arr, size);  
  
    // Display the list  
    cout << "Initial Linked List: ";  
    printLinkedList(head);  
  
    // Print nodes alternately  
    // printAlternately(head);    // printLinkedList(reverse(head));    // head = deleteHead(head);    // deleteTail(head);    cout << findSecondLastNode(head)->data << endl;;  
    printLinkedList(head);  
  
  
  
  
    return 0;  
}
```


### I'll check if this code created by me is correct for left shift operations

```cpp
/**

* Definition for singly-linked list.

* struct ListNode {

* int val;

* ListNode *next;

* ListNode() : val(0), next(nullptr) {}

* ListNode(int x) : val(x), next(nullptr) {}

* ListNode(int x, ListNode *next) : val(x), next(next) {}

* };

*/

class Solution {

public:

ListNode* rotateRight(ListNode* head, int k) {

if(!head) return nullptr;

int i=0;

ListNode *temp = head;

  

while(temp->next) {

temp = temp->next;

}

temp->next = head;

head = temp;

ListNode *newHead;

for (int i=0; i<k-1; i++) {

temp = temp->next;

}

newHead = temp->next;

temp->next = nullptr;

return newHead;

}

};
```

