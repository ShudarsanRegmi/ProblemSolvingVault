
# Reverse Linked List

Solved 

Easy

Given the beginning of a singly linked list `head`, reverse the list, and return the new beginning of the list.

**Example 1:**

```java
Input: head = [0,1,2,3]

Output: [3,2,1,0]
```

Copy

**Example 2:**

```java
Input: head = []

Output: []
```

Copy

**Constraints:**

- `0 <= The length of the list <= 1000`.
- `-1000 <= Node.val <= 1000`

---


![[LinkedList/LinkedList.excalidraw.md#^group=InlCx6EBc7KtIOCfoFxsu|100%]]

```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */

class Solution {
    // o -> o -> o -> o -> null
public:
    ListNode* reverseList(ListNode* head) {
        ListNode *curr = head;
        ListNode *prev = nullptr;
        ListNode *next;

        while(curr != nullptr) {
            next = curr->next;
            curr->next = prev;
            prev = curr;
            curr = next;
        }
        return prev;
    }
};

```

*Time Complexity:* $O(n)$
*Space Complexity:* $O(1)$

## Recursive Approach: 
<p style='color:red;font-size:20px'>I'll do it later</p>


