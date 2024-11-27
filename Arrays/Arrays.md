Here I'll Keep Arrays Note
### Some Core Concepts on Arrays

- No. of SubArrays = $n(n+1)/2$


### Naive Approach to Find SubArrays

```cpp
#include <iostream>

using namespace std;

int main() {
    int arr[5] = {1,2,3,4,5};
    for (int i=0; i<5; i++) {
        for (int j=i; j<5; j++) {
            for(int k=i; k<=j; k++) {
                cout << arr[k] << '\t';
            }
            cout << endl;
        }
        cout << endl;
    }
}
```


