

```
Input: arr[] = {4, 10, 3, 5, 1}  
Output: Corresponding Max-Heap:

       10  
     /   \  
   5     3  
  /  \  
4    1

Input: arr[] = {1, 3, 5, 4, 6, 13, 10, 9, 8, 15, 17}  
Output: Corresponding Max-Heap:

                 17  
              /      \  
          15         13  
         /    \      /  \  
       9      6    5   10  
     / \    /  \  
   4   8  3    1
```

**Note**
- Root is at index 0 in array.
- Left child of i-th node is at (2*i + 1)th index.
- Right child of i-th node is at (2*i + 2)th index.
- Parent of i-th node is at (i-1)/2 index.

