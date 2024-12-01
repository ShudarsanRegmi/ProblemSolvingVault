

```cpp
#include <iostream>  
  
using namespace std;  
  
int main() {  
    int arr1[] = {1,3,5,7,9,15,16,17,19};  
    int arr2[] = {1,4,5,6,9,10};  
  
    int n1 = sizeof(arr1) / sizeof(arr1[0]);  
    int n2 = sizeof(arr2) / sizeof(arr2[0]);  
  
    int n = n1+n2;  
  
    int arr[n];  
    int p3 = 0;  
  
    int p1=0,p2=0;  
  
    int i = 0;  
    while (i<=n) {  
        if (arr1[p1] < arr2[p2]) {  
            arr[p3] = arr1[p1];  
            p1++;  
            p3++;  
        }else {  
            arr[p3] = arr2[p2];  
            p3++;  
            p2++;  
        }  
        // if one of the array get exhausted then copy remaining to others...  
        if (p1 == n1) {  
            while (p2 <= n2) {  
                arr[p3] = arr2[p2];  
                p2++;  
                p3++;  
            }  
            break;  
        }  
        if (p2 == n2) {  
            while (p1 <=n1) {  
                arr[p3] = arr1[p1];  
                p1++;  
                p3++;  
            }  
            break;  
        }  
  
        i++;  
    }  
    // print the merged array  
    for (int i=0; i<n;i++) {  
        cout << arr[i] << '\t';  
    }  
    cout << endl;  
    return 0;  
}
```

[[Arrays]]