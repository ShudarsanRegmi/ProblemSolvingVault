# Daily Temperatures

Medium

You are given an array of integers `temperatures` where `temperatures[i]` represents the daily temperatures on the `ith` day.

Return an array `result` where `result[i]` is the number of days after the `ith` day before a warmer temperature appears on a future day. If there is no day in the future where a warmer temperature will appear for the `ith` day, set `result[i]` to `0` instead.

**Example 1:**

```java
Input: temperatures = [30,38,30,36,35,40,28]

Output: [1,4,1,2,1,0,0]
```

Copy

**Example 2:**

```java
Input: temperatures = [22,21,20]

Output: [0,0,0]
```

Copy

**Constraints:**

- `1 <= temperatures.length <= 1000`.
- `1 <= temperatures[i] <= 100`

---

## My Solution - I
```cpp
class Solution {
 public:
  vector<int> dailyTemperatures(vector<int>& temps) {
    int n = temps.size();
    vector<int> htemps;
    for (int i = 0; i < n - 1; i++) {
      int c = 0;
      int d = c;
      for (int j = i + 1; j < n; j++) {
        c++;
        if (temps[j] > temps[i]) {
          d = c;
          break;
        }
      }
      htemps.push_back(d);
    }
    htemps.push_back(0);
    return htemps;
  }
};

```

<p style='color:red; font-size: 20px'>Got Tmeout Error </p>
![[Stack/Stack.excalidraw.md#^group=X0nsrQvYWIGwErAE6o93i|100%]]

### Looking for a way to optimize

![[Stack/Stack.excalidraw.md#^group=-HvDVezZn7HHHpswtjre0|100%]]


