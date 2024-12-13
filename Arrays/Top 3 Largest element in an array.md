
```cpp
class Solution {
public:
    vector<int> getThreeLargest(vector<int>& arr) {
        int l1 = INT_MIN, l2 = INT_MIN, l3 = INT_MIN;
        int e;
        
        for (int i = 0; i < arr.size(); i++) {
            e = arr[i];
            
            if (e > l1) {
                l3 = l2;
                l2 = l1;
                l1 = e;
            } else if (e > l2 && e < l1) {
                l3 = l2;
                l2 = e;
            } else if (e > l3 && e < l2) {
                l3 = e;
            }
        }
        
        if (l1 == INT_MIN) {
            return {};
        } else if (l2 == INT_MIN) {
            return {l1};
        } else if (l3 == INT_MIN) {
            return {l1, l2};
        } else {
            return {l1, l2, l3};
        }
```


#geeksforgeeks 

